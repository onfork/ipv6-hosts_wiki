> 授人以鱼，不如授人以渔。

如 [[Google]] 页面所述，Google 的 IP 分为两大类，[[1e100.net]] 和 [[sn-domains]]。

前者用于动态域名解析，提供普通服务，如 Google Search，Gmail，Google Maps。  
后者用于 [[Youtube]]，Google Docs，Android Clients (Google Play) 等需要大量存储空间的服务的缓存。

下面针对这两种 IP 介绍自定义方法。

## 一、加速或者添加新开放域名 (1e100)

`snippets/1e100.txt` 这个文件并没有合并在最终生成的 hosts 中，它列出了目前为止 Google 所有的用于动态域名解析的服务器。

在动态 IP 对应的域名出问题时，你可以从文件中任选一个 IP (当然选最快的)，将域名重定向至此 IP 即可，仅有极少数域名例外。

> P.S. 这个文件中的 IP 可以用于 goagent。

* 加速

  方法可以阅读页面[如何加速](How-to-speed-up)。

* 添加新域名

  比如最近新推出的服务 Project Fi。  
  先获取其域名 `fi.google.com`，hosts 文件中并无此域名，所以有可能无法访问。  
  可以使用 `dig` 向 DNS 查询其对应的 IPv6，也可以直接使用其他域名的地址如 `2607:f8b0:4007:804::1000` 将其进行重定向。  
  形成

  ```
  2607:f8b0:4007:804::1000 fi.google.com
  ```
  这样的条目，按字母序加入到 hosts 文件中就行了。


**原理：**

Google 在自己的网络中应用了 任播 ([Anycast](https://en.wikipedia.org/wiki/Anycast)) 技术。简单来说，就是服务请求方并不关心服务提供方具体是哪一台主机，根据来源 IP 和数据包 (包含 URL 信息)，任意一台服务器都可以提供多种服务。

比如向 `8.8.8.8` 进行 DNS 查询时，不同的来源 IP 会得到不同的查询结果。
```
dig @8.8.8.8 +vc +short aaaa www.google.com
```
在大陆，可能会得到 `2404:6800:4005:808::2004`  
而在洛杉矶，就可能是这样的结果 `2607:f8b0:4007:804::1014`。

一个是香港的服务器，一个是洛杉矶的服务器。

向任意一个服务器都可以请求完整的 Google 服务。

因此你可以把 **搜索**、**Gmail**、**地图** 全部重定向到同一个 IP 而不会受影响。
```
2607:f8b0:4007:804::1014 www.google.com
2607:f8b0:4007:804::1014 mail.google.com
2607:f8b0:4007:804::1014 maps.google.com
```
并且可以通过切换 IP 段来加速访问。


但是有一种服务例外，YouTube。

## 二、增加 googlevideo 服务器 (sn domains)

虽然你向任意一台服务器都可以请求到全网的视频 (只要视频本身并无地域限制)，但是访问 YouTube 并不像普通服务一样直接进行访问，而是会进行 redirect。

在观看一个视频时，大致步骤如下：
  1. 浏览器首先向 youtube.com 发起请求，youtube.com 会根据来源 IP 所属的 IP 段向客户端分配一个服务器 (通常会选择性能最好的节点，但是因为某些原因，会出现 [Issue #8](https://github.com/lennylxx/ipv6-hosts/issues/8) 描述的现象)，比如 `r1---sn-gxuxapu-hm2e.googlevideo.com`。
  2. 客户端向`r1.sn-gxuxapu-hm2e` 请求真正的视频文件。  
     如果此服务器无法访问，youtube.com 进行第二次 redirect，如 `r8---sn-o097znel.googlevideo.com`。
  3. 客户端向第二次分配的服务器 `r8.sn-o097znel` 请求视频文件。
  4. 如果第二次分配的服务器还无法访问，那么失败。

第一步是根据来源 IP 进行导向的，所以你无法通过自己重定向来加速，除非用代理访问 youtube.com 这个域名 (间接改变来源 IP)，然后直连分配的 googlevideo 服务器。

可以访问 `https://redirector.googlevideo.com/report_mapping` 来查询 Youtube 为你分配的节点。

> 扩展阅读，[Youtube 工作原理](http://www.slideshare.net/Netmanias/netmanias20120416ggc-operation-for-you-tube-part-1-kt-en)。

Google 不定期地会增加一批 `googlevideo.com` 服务器。

只要知道了这批服务器域名中任意一个的前缀，比如最近新增的 `f5f` (解码之后为 waw 华沙) 就可以利用脚本穷举出所有 IP。

**具体步骤：**

1. 生成所有 r2 开头的域名。

   ```
   $ ./list-sn.py f5f > f5f.txt
   ```
2. 刷新这批域名的 IP，目的是筛选出有效组号 (跟随在`f5f`之后的 5 位编码)。

   ```
   $ ../update_hosts.py f5f.txt -o f5f-new.txt -n 128
   ```
3. 生成有效组号对应的所有可能域名。

   ```
   $ ./list-sn-all.py f5f-new.txt > f5f-all.txt
   ```
4. 获取这些域名对应的 IPv6 地址。

   ```
   $ ../update_hosts.py f5f-all.txt -o f5f-hosts.txt -n 128
   ```
5. 利用编辑器的正则匹配功能删除所有 `#` 开头的行。

   ```
   Regex: #((?!-)[A-Za-z0-9-]{1,63}(?<!-)\.)+[A-Za-z]{2,6}
   ```
6. 将得到的文件按照 IPv6 地址升序添加进 `snippets/08_googlevideo.txt` 文件。
7. 更新 hosts 文件。

   ```
   $ rm hosts && ./merge_hosts.sh hosts
   ```