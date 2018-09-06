本项目的主要目的即为了对 IPv6 资源进行加速访问。

如果你访问 Google 太慢，可以将 Google 的动态 IPv6 前缀换为其他的地址段(如香港，日本等)。  
这些动态 IP 大多分布在 snippets:[01]-[02]-[03]-[04]-[05]-[06] 中。

如可以将 `2404:6800:400a: (大阪)` 换为 `2404:6800:4005: (香港)`。  

~~但是目前香港的延时太高，有 `300 ms`。~~

---

默认情况下，如果你使用了 Google DNS (如 `8.8.8.8`)，查询到的 Google IP 基本上全是香港的。
```
# dig @8.8.8.8 www.google.com aaaa +vc +short 
2404:6800:4005:801::1010
```
这是因为 Google 的服务器会根据查询的来源 IP，试图将你引导至距离你最近(性能最好)的节点，针对大陆来说就是香港。  
~~但是由于国内 IPv6 路由的奇葩设置，目前国内几乎所有 IPv6 流量均从北京出，在洛杉矶上岸，然后再去往其他地区。
虽然香港/日本在物理距离上更近，但是去往香港，日本的流量会绕太平洋转一圈，所以将 Google 域名解析到香港 IP 并不会加速，反而具有高延迟。~~

~~因此当前的 hosts (主要是 Google 域名) 使用了最快的位于**洛杉矶**的服务器~~，北京教育网延时约为 `160 ms`。

既然已经将域名重定向至洛杉矶，我们还可以得知，hosts 文件中大部分 [sn 编码域名](sn-domains)(主要用于 [[YouTube]] 视频服务，对应静态 IP)就都没有存在的必要了，只保留属于**洛杉矶**的地址段即可，也就是 `2001:4860:4007::/48` 和 `2607:f8b0:4007::/48`。  
不过为了保持完整性，本项目还是列出了所有域名。

---

使用 `traceroute` 命令测试结果：
```
traceroute to hkg03s09-in-x01.1e100.net (2404:6800:4005:800::1001), 30 hops max, 80 byte packets
 1  [blocked]  4.563 ms  4.488 ms  5.638 ms
 2  * * *
 3  * * *
 4  [blocked]  8.156 ms  8.125 ms  8.085 ms
 5  [blocked]  8.045 ms  8.052 ms  7.972 ms
 6  [blocked]  7.813 ms  6.761 ms  6.582 ms
 7  [blocked]  6.546 ms  6.503 ms  6.455 ms
 8  * * *
 9  [blocked]  9.580 ms * *
10  2001:252:0:100::2 (2001:252:0:100::2)  10.276 ms  10.244 ms  10.209 ms
11  2001:252:0:302::2 (2001:252:0:302::2)  156.054 ms  152.959 ms *
12  10gigabitethernet16-5.core1.lax2.he.net (2001:470:0:2a2::1)  155.502 ms  155.467 ms  156.571 ms
13  2001:504:13::210:41 (2001:504:13::210:41)  156.421 ms 2001:4860:1:1:0:1b1b:0:19 (2001:4860:1:1:0:1b1b:0:19)  152.055 ms  152.017 ms
14  2001:4860::1:0:6b02 (2001:4860::1:0:6b02)  156.456 ms 2001:4860::1:0:6b01 (2001:4860::1:0:6b01)  160.030 ms 2001:4860::1:0:6b02 (2001:4860::1:0:6b02)  154.825 ms
15  2001:4860::8:0:7a19 (2001:4860::8:0:7a19)  154.645 ms  154.735 ms  153.494 ms
16  2001:4860::1:0:6302 (2001:4860::1:0:6302)  251.198 ms 2001:4860::1:0:75 (2001:4860::1:0:75)  251.154 ms 2001:4860::1:0:6302 (2001:4860::1:0:6302)  249.984 ms
17  2001:4860::1:0:16 (2001:4860::1:0:16)  303.791 ms  304.211 ms  300.266 ms
18  2001:4860:0:1::6db (2001:4860:0:1::6db)  299.651 ms  302.699 ms  301.075 ms
19  2404:6800:8000::9 (2404:6800:8000::9)  299.730 ms  299.153 ms 2404:6800:4005:800::14 (2404:6800:4005:800::14)  304.403 ms
```
可以看到结果中有一个关键节点 `10gigabitethernet16-5.core1.lax2.he.net (2001:470:0:2a2::1)`，这是 Hurricane Electric 位于洛杉矶的路由器。

~~因此如何加速就显而易见了，选择位于洛杉矶的 DNS 即可，如 `tserv1.lax1.he.net`。~~

本项目提供了一个[更新 hosts 的脚本]，你可以这样使用：
```
./update_hosts.py snippets/01_google.txt -s ordns.he.net -o new_google.txt -n 128 -c 
```
不过你没必要自己更新，因为除了可以在 DNS 直接查询到的地址，hosts 中还存在一部分需要手动指定 IP 的域名，每次更新过后需要额外添加。

* 只有在你的网络环境不需要经过洛杉矶就能到达香港/日本时，你才需要指定其他的 DNS 重新更新 hosts。
* **附**：每次使用 `update_hosts.py` 更新过后，需要手动指定 IP 的域名列表
  ```
  2404:6800:4005:800::2000 scholar.google.com
  2404:6800:4005:800::2003 scholar.google.com.hk
  2404:6800:4005:800::2003 scholar.google.com.tw
  2404:6800:4005:800::2000 android.clients.google.com
  2404:6800:4005:800::2000 console.developer.google.com
  2404:6800:4008:c06::52 console.developers.google.com
  2404:6800:4008:c06::7b wifi.google.com
  2404:6800:4005:800::2000 www.google.org
  2404:6800:4005:800::2000 www.chromium.org
  2404:6800:4005:800::2000 dev.chromium.org
  2404:6800:4005:800::2000 blog.chromium.org

  2404:6800:4005:800::2000 android.l.google.com
  2404:6800:4005:800::2000 scholar.l.google.com
  2404:6800:4008:c06::7b wifi.l.google.com
  ```
  

---

更多信息请参考 [[1e100.net]] 和 [[YouTube]]。


[01]:               https://github.com/lennylxx/ipv6-hosts/blob/master/snippets/01_google.txt
[02]:               https://github.com/lennylxx/ipv6-hosts/blob/master/snippets/02_l.google.txt
[03]:               https://github.com/lennylxx/ipv6-hosts/blob/master/snippets/03_adwords.txt
[04]:               https://github.com/lennylxx/ipv6-hosts/blob/master/snippets/04_android.txt
[05]:               https://github.com/lennylxx/ipv6-hosts/blob/master/snippets/05_bigcache.txt
[06]:               https://github.com/lennylxx/ipv6-hosts/blob/master/snippets/06_googleusercontent.txt
[更新 hosts 的脚本]: https://github.com/lennylxx/ipv6-hosts/blob/master/update_hosts.py