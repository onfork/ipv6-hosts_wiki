As [[Google]] described, GGC is an important part of Google CDN, provided by ISP
and Google.

> Inquire the GGC servers assigned to you at
  https://redirector.googlevideo.com/report_mapping


**Pattern** of GGC server domains

    r?---sn-[isp name]-[loc][x].googlevideo.com

1. `[isp name]` is the encoded ISP name, conversion rules are same as
    [[SN domains]], the length varies.
2. `[loc]` is the encoded [IATA airport code], same conversion rules, the length
    is `3`.
3. `[x]` is the encoded number of server group, length is `1` or `2`.

> See [conversion code].

Common GGC server domains conversion result table
```
| IPv6 Prefix              | ISP NAME           | GGC Serial Number  |
| ------------------------ | ------------------ | ------------------ |
| 2001:660:302a:1::/64     | renater-cdg1       | gxo5uxg-jqbe       |
| 2001:7f8:49:1::/64       | ronix-otp1         | gvopm-vu2e         |
| 2001:f18:113:14::/64     | nctu-tpe2          | oju0-u2xl          |
| 2001:f40:0:5::/64        | timedotcom-kul2    | uphxqvujvh-30al    |
| 2001:1438:0:1006::/64    | versatel-dtm1      | 8xgn5uxa-quhe      |
| 2001:16d8:4:7::/64       | availo-bma1        | 585pav-ch5e        |
| 2001:1900:210a::/64      | lvlt-ewr1          | a8au-xfge          |
| 2001:1900:2200:f::/64    | lvlt-iad4          | a8au-p5qz          |
| 2001:1900:2200:10::/64   | lvlt-bos1          | a8au-cvne          |
| 2001:1900:2200:20::/64   | lvlt-slc1          | a8au-naje          |
| 2001:1900:2200:80::/64   | lvlt-bna1          | a8au-co5e          |
| 2001:1900:229e::/64      | lvlt-lax1          | a8au-a5me          |
| 2001:1a80:100:1c::/64    | qsc-fra1           | 9nj-4g5e           |
| 2001:1bc8:100:1b::/64    | nebula-hel1        | oxc0a5-ixae        |
| 2001:1bd0:1:12::/64      | retelit-mxp1       | gxuxapu-hm2e       |
| 2001:4350:0:12::/64      | ati-tun1           | 5up-u0oe           |
| 2001:4350:2048:12::/64   | ati-tun2           | 5up-u0ol           |
| 2001:4490:3ffc:4::/64    | bsnl-jai1          | cnoa-w5pe          |
| 2001:4490:3ffd:1::/64    | bsnl-pat1          | cnoa-25ue          |
| 2001:4490:3ffd:8001::/64 | bsnl-maa2          | cnoa-h55l          |
| 2001:4498:a:200::/64     | timedotcom-kul1    | uphxqvujvh-30ae    |
| 2001:b000:182:c100::/64  | phinet-tsa1        | 2ipoxu-un5e        |
| 2001:b000:182:c101::/64  | phinet-tsa2        | 2ipoxu-un5l        |
| 2001:b032:2101::/64      | hinet-tsa4         | ipoxu-un5z         |
| 2001:b032:5d00::/64      | hinet-tpe3         | ipoxu-u2xs         |
| 2400:9800:0:f021::/64    | excelcom-cgk1      | xmjxajvh-jb3e      |
| 2400:c700:2000:2::/64    | ideacellular-pnq2  | pqx5jxaa0a5g-2o9l  |
| 2402:9200:18:2::/64      | waia-mel1          | f5p5-hxae          |
| 2403:5000:171:24::/64    | hgc-hkg3           | ibj-i3bs           |
| 2404:8000:10:22::/64     | biznet-cgk1        | cp1oxu-jb3e        |
| 2406:e100:0:1::/64       | ixsforall-mnl1     | pmn4vg5aa-hoae     |
| 2407:0:0:10::/64         | indosat-cgk1       | poqvn5u-jb3e       |
| 2407:0:0:11::/64         | indosat-cgk2       | poqvn5u-jb3l       |
| 2620:4b::/64             | wpgix-ywg1         | f2bpm-tfbe         |
| 2620:11a:a00c::/64       | mice-msp1          | hpjx-hn2e          |
| 2620:11a:a00e::/64       | google-msp1        | bvvbax-hn2e        |
| 2620:11a:a00e:1::/64     | google-msp2        | bvvbax-hn2l        |
| 2806:10a0:cfff:3::/64    | uninet-pbc6        | 0opoxu-2cjd        |
| 2a00:800:1100::/64       | teletwo-vie1       | uxaxufv-8pxe       |
| 2a00:800:1100:1::/64     | teletwo-vie2       | uxaxufv-8pxl       |
| 2a00:ff0:1234:2::/64     | interlan-otp2      | pouxga5o-vu2l      |
| 2a00:1e48:1:b::/64       | transtelecom-ovb1  | ug5onuxaxjvh-v8ce  |


```

[conversion code]:  https://github.com/lennylxx/ipv6-hosts/blob/master/tools/conv.py
[IATA airport code]: https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code
