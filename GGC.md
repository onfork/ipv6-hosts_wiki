如 [Google] 页面所述，GGC 是 Google CDN 的一部分，由 ISP 和 Google 共同提供。

> 查看分配给你的 GGC https://redirector.googlevideo.com/report_mapping


GGC 服务器域名以 SN 编码的形式存在，格式如下：

    r?---sn-[isp name]-[loc][x].googlevideo.com

1. `[isp name]` 是经过转换的 ISP 名称，转换规则与 [SN 编码]相同。长度不等。
2. `[loc]` 是 [IATA 机场编码]转换后的结果，转换规则同上，长度为 3 位。
3. `[x]` 服务器编号，由数字转换而来，1 位。

常见域名转换前后对照表
```
| IPv6 Prefix              | ISP NAME           | GGC Serial Number  |
| ------------------------ | ------------------ | ------------------ |
| 2001:660:302a:1::/64     | renater-cdg1       | gxo5uxg-jqbe       |
| 2001:7f8:49:1::/64       | ronix-otp1         | gvopm-vu2e         |
| 2001:f18:113:14::/64     | nctu-tpe2          | oju0-u2xl          |
| 2001:f40:0:5::/64        | timedotcom-kul2    | uphxqvujvh-30al    |
| 2001:1438:0:1006::/64    | versatel-dtm1      | 8xgn5uxa-quhe      |
| 2001:1900:2200:f::/64    | lvlt-iad4          | a8au-p5qz          |
| 2001:1900:2200:10::/64   | lvlt-bos1          | a8au-cvne          |
| 2001:1900:2200:20::/64   | lvlt-slc1          | a8au-naje          |
| 2001:1900:2200:80::/64   | lvlt-bna1          | a8au-co5e          |
| 2001:1bc8:100:1b::/64    | nebula-hel1        | oxc0a5-ixae        |
| 2001:1bd0:1:12::/64      | retelit-mxp1       | gxuxapu-hm2e       |
| 2001:4350:0:12::/64      | ati-tun1           | 5up-u0oe           |
| 2001:4350:2048:12::/64   | ati-tun2           | 5up-u0ol           |
| 2001:4490:3ffd:8001::/64 | bsnl-maa2          | cnoa-h55l          |
| 2001:4498:a:200::/64     | timedotcom-kul1    | uphxqvujvh-30ae    |
| 2001:b000:182:c100::/64  | phinet-tsa1        | 2ipoxu-un5e        |
| 2001:b000:182:c101::/64  | phinet-tsa2        | 2ipoxu-un5l        |
| 2001:b032:2101::/64      | hinet-tsa4         | ipoxu-un5z         |
| 2400:9800:0:f021::/64    | excelcom-cgk1      | xmjxajvh-jb3e      |
| 2400:c700:2000:2::/64    | ideacellular-pnq2  | pqx5jxaa0a5g-2o9l  |
| 2403:5000:171:24::/64    | hgc-hkg3           | ibj-i3bs           |
| 2404:8000:10:22::/64     | biznet-cgk1        | cp1oxu-jb3e        |
| 2406:e100:0:1::/64       | ixsforall-mnl1     | pmn4vg5aa-hoae     |
| 2407:0:0:10::/64         | indosat-cgk1       | poqvn5u-jb3e       |
| 2407:0:0:11::/64         | indosat-cgk2       | poqvn5u-jb3l       |
| 2620:11a:a00c::/64       | mice-msp1          | hpjx-hn2e          |
| 2620:11a:a00e::/64       | google-msp1        | bvvbax-hn2e        |
| 2620:11a:a00e:1::/64     | google-msp2        | bvvbax-hn2l        |
| 2806:10a0:cfff:3::/64    | uninet-pbc6        | 0opoxu-2cjd        |
| 2a00:800:1100::/64       | teletwo-vie1       | uxaxufv-8pxe       |
| 2a00:800:1100:1::/64     | teletwo-vie2       | uxaxufv-8pxl       |
| 2a00:1e48:1:b::/64       | transtelecom-ovb1  | ug5onuxaxjvh-v8ce  |
```


[Google]: https://github.com/lennylxx/ipv6-hosts/wiki/Google
[SN 编码]: https://github.com/lennylxx/ipv6-hosts/wiki/sn-domains
[IATA 机场编码]: https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code
