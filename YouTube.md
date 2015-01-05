> YouTube 域名规则

*.c.youtube.com 和 *.googlevideo.com 指向的地址是相同的。  
下文只列出 *.googlevideo.com。

1. 域名重定向地址
-----------------

    v?.lscache?.googlevideo.com
    v?.nonxt?.googlevideo.com
    tc.v?.cache?.googlevideo.com

经过实践，以上六种域名都是`bandaid-redirector.l.google.com`的aliase，
由重定向服务器分配IP，地址不固定。  
但是所有地址在某一时间段内分配的IP都是同一个。  
每种域名有8组，每组域名24个，v1-v24。

2. 固定地址
-----------

    v?.cache?.googlevideo.com

以上两种域名指向的IP相同，为固定IP。
目前已知的前缀均为**2a00:1450:400e::/48**，IPv6第4段取值范围400-407，
第8段取值范围10-17。
每组域名共8个，v1-v8。

3. 前缀限定地址
---------------

    r?.xxx??s??.googlevideo.com
    r?---xxx??s??.googlevideo.com

以上四种域名指向的IP相同，为固定IP，xxx([IATA 机场编码])决定服务器地理位置。  
IP段和IATA机场编码可参照 [[1e100.net]] 的[服务器部署信息表格]。  
每组域名共20个，r1-r20。   

4. SN 编码地址
--------------

    r?.sn-xxxxxxxx.googlevideo.com
    r?---sn-xxxxxxxx.googlevideo.com

最近出现的新域名，固定IP，xxxxxxxx为八位编码，含义未知，但编码比较有规律，
初步猜测是做了 hash。  
每组域名共20个，r1-r20。对应的 IPv6 地址第8段取值范围则是0x6-0x19。  

> 此规则同样适用于 *.gvt1.com 和 *.c.android.clients.google.com 域名。

**栗子**

    2001:4860:4001:7::6 r1---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::7 r2---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::8 r3---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::9 r4---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::a r5---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::b r6---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::c r7---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::d r8---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::e r9---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::f r10---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::10 r11---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::11 r12---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::12 r13---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::13 r14---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::14 r15---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::15 r16---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::16 r17---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::17 r18---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::18 r19---sn-nwj7kned.googlevideo.com
    2001:4860:4001:7::19 r20---sn-nwj7kned.googlevideo.com

**下面是五个已知 sn 编码表格**  
  * 表头为 IPv6 前3段(48位)，第 1 列为 IPv6 第4段。
  * 左上角数字(20)代表每个编码域名的个数，中括号中数字为特别标明数量。
  * 表格第一行为 [IATA 机场编码]和城市名
  * 上面的栗子可以在第一个表格的第7行找到  

| 20|2001:4860:4001|2001:4860:4002|2001:4860:4007|
|---|--------------|--------------|--------------|
|   |UNKNOWN       |UNKNOWN       |LAX 洛杉矶    |
|  0|              |              |              |
|  1|nwj7kner      |              |              |
|  2|nwj7knee      |              |              |
|  3|nwj7knel      |              |              |
|  4|nwj7knes      |q4f7dn7r      |a5m7ln7s      |
|  5|nwj7knez      |q4f7dn7y      |a5m7ln7z      |
|  6|nwj7kne6      |q4f7dne7      |a5m7ln76      |
|  7|nwj7kned      |q4f7dnee      |a5m7ln7d      |
|  8|nwj7knek      |              |              |
|  9|              |q4f7dnel      |              |
|  a|              |q4f7dnes      |              |
|  b|              |q4f7dnez      |              |
|  c|              |q4f7dne6      |              |
|  d|o097zne7      |              |              |
|  e|o097znee      |              |              |
|  f|o097znel      |              |              |
| 10|o097znes      |              |a5m7ln7k      |
| 11|o097znez      |              |a5m7ln7r      |
| 12|o097zne6      |              |a5m7ln7y      |
| 13|o097zned      |              |              |
| 14|o097znek      |              |              |


| 12|2401:3800:4001|
|---|--------------|
|   |UNKNOWN       |
|  0|              |
|  1|              |
|  2|2x37ln7e      |
|  3|2x37ln7l      |
|  4|              |
|  5|2x37ln7s      |
|  6|2x37ln7z      |


| 20|2404:6800:4001|2404:6800:4002|2404:6800:4003|2404:6800:4005|2404:6800:4007|
|---|--------------|--------------|--------------|--------------|--------------|
|   |KUL 吉隆坡    |DEL 新德里    |SIN 新加坡    |HKG 香港      |MAA 金奈      |
|  0|              |qxa7en7e      |npo7en7d      |i3b7rn7k [6]  |h557sn7r      |
|  1|              |qxa7en7l      |npo7en7k      |i3b7rn7r [6]  |h557sn7y      |
|  2|              |qxa7en7s      |npo7en7r      |i3b7rn7y [6]  |h557sne7      |
|  3|              |qxa7en7z      |npo7en7y      |i3b7rne7 [6]  |h557snee      |
|  4|              |              |npo7ene7      |i3b7sn76      |h557snel      |
|  5|              |              |npo7enee      |i3b7sn7d      |h557snes      |
|  6|              |              |npo7enel      |i3b7sn7k      |h557snez      |
|  7|              |              |npo7enes      |i3b7sn7r      |h557sne6      |
|  8|30a7en7s      |              |npo7zn7s [6]  |i3b7snek      |h557sned      |
|  9|30a7en76      |              |npo7zn7z [6]  |i3b7sner      |h557snek      |
|  a|              |              |              |i3b7sney      |              |
|  b|              |              |              |i3b7snl7      |              |
|  c|              |              |              |i3b7sn7e      |              |
|  d|              |              |              |i3b7sn7l      |              |
|  e|              |              |              |i3b7sn7s      |              |
|  f|              |              |              |i3b7sn7z      |              |
| 10|30a7en7z      |              |              |i3b7rnee [6]  |              |
| 11|30a7en7d      |              |              |i3b7rnel [6]  |              |


| 20|2607:f8b0:4000|2607:f8b0:4001|2607:f8b0:4004|2607:f8b0:4005|2607:f8b0:4006|2607:f8b0:4007|2607:f8b0:4008|2607:f8b0:4009|2607:f8b0:400a|2607:f8b0:4012|
|---|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
|   |DFW 达拉斯    |UNKNOWN       |IAD 华盛顿    |NUQ 山景城    |LGA 纽约      |LAX 洛杉矶    |MIA 迈阿密    |ORD 芝加哥    |SEA 西雅图    |QRO 克雷塔罗  |
|  0|              |              |              |nwj7kney      |              |a5mekn7d [6]  |              |vgqsen7e      |nx57ynee      |9gv7en7e      |
|  1|              |              |p5qlsnsd [6]  |nwj7knl7      |              |              |              |vgqs7nes [6]  |nx57yn7s      |9gv7en7l      |
|  2|q4f7dner      |              |p5qlsnsk [6]  |              |ab5l6nl6      |a5m7znez      |              |vgqs7nez [6]  |nx57yn7z      |9gv7en7s      |
|  3|q4f7dney      |              |              |              |              |a5m7zne6      |              |vgqs7ne6      |nx57yn76      |9gv7en7z      |
|  4|q4f7dnl7      |              |              |o097znl7      |ab5l6nss      |a5m7zned      |              |vgqs7ned      |nx57yn7d      |9gv7en76      |
|  5|q4f7dnle      |              |              |o097znle      |              |a5m7znek      |              |vgqs7nek      |nx57yn7k      |9gv7en7d      |
|  6|              |              |              |o097znll      |              |a5m7zne7      |              |vgqs7ner      |nx57yn7r      |9gv7en7k      |
|  7|              |              |              |o097znls      |              |a5m7znee      |              |vgqsenek [6]  |nx57yn7y      |9gv7en7r      |
|  8|              |              |p5qlsn7e      |              |ab5l6n7e      |a5m7znel      |              |vgqsener [6]  |nx57yne7      |              |
|  9|              |              |p5qlsn7l      |              |ab5l6n7l      |a5m7znes      |              |vgqs7ney [6]  |nx57ynel      |              |
|  a|q4f7dnsd      |              |p5qlsn7s      |              |ab5l6nsd      |a5mekn7r [6]  |              |vgqsen7y      |nx57ynes      |              |
|  b|q4f7dnsk      |              |p5qlsn7z      |nwj7knls      |              |a5mekn7y [6]  |              |vgqsene7      |nx57ynez      |              |
|  c|              |              |              |nwj7knlz      |ab5l6nsk [6]  |a5mekne7 [6]  |hp57kn7e [6]  |vgqsen7l      |nx57yney      |              |
|  d|              |              |              |              |              |a5meknee [6]  |hp57kn7l [6]  |vgqsen7s      |nx57ynl7      |              |
|  e|              |              |              |              |ab5l6n7s      |a5meknel [6]  |hp57kn7s [6]  |vgqsen7z      |nx57ynle      |              |
|  f|q4f7dnz6      |              |              |              |ab5l6n7z      |a5meknes [6]  |hp57kn7z [6]  |vgqsen76      |nx57ynll      |              |
| 10|              |              |p5qlsn7y      |              |ab5l6n76      |a5m7ln7k      |hp57kn76      |vgqs7nl7 [6]  |              |              |
| 11|              |              |p5qlsne7      |              |ab5l6n7d      |a5m7ln7r      |hp57kn7d      |vgqseney [6]  |              |              |
| 12|              |              |p5qlsnee      |              |ab5l6n7k      |a5m7ln7y      |hp57kn7k      |vgqsenl7 [6]  |              |              |
| 13|              |              |p5qlsnel      |              |ab5l6n7r      |a5m7lne7      |hp57kn7r      |              |              |              |
| 14|q4f7sn7e [6]  |              |p5qlsnes      |              |ab5l6n7y      |a5m7lnee      |hp57kn7y      |              |              |              |
| 15|q4f7sn7l [6]  |              |p5qlsnez      |              |ab5l6ne7      |a5m7lnel      |hp57kne7      |              |              |              |
| 16|q4f7sn7s [6]  |              |p5qlsne6      |              |ab5l6nee      |a5m7lnes      |hp57knee      |              |              |              |
| 17|q4f7sn7z [6]  |              |p5qlsned      |              |ab5l6nel      |a5m7lnez      |hp57knel      |vgqsen7d      |              |              |
| 18|q4f7sn76 [6]  |              |p5qlsney      |              |ab5l6nes      |a5m7lne6      |              |vgqsen7k      |              |              |
| 19|q4f7sn7d [6]  |              |p5qlsnl7      |              |ab5l6nez      |a5m7lned      |              |vgqsen7r      |              |              |
| 1a|q4f7sn7k [6]  |              |p5qlsnle      |              |ab5l6ne6      |a5m7lnek      |              |vgqsenee      |              |              |
| 1b|q4f7sn7r [6]  |              |p5qlsnll      |              |ab5l6ned      |a5m7lner      |              |vgqsenel      |              |              |
| 1c|q4f7sn7y      |              |              |              |ab5l6nek      |              |              |vgqs7n7e      |              |              |
| 1d|q4f7sne7      |              |              |              |ab5l6ner      |              |              |vgqs7n7l      |              |              |
| 1e|q4f7snee      |              |p5qlsnss      |              |ab5l6ney      |              |              |vgqs7n7s      |              |              |
| 1f|q4f7snel      |              |              |              |ab5l6nl7      |              |              |vgqs7n7z      |              |              |
| 20|q4f7snes      |              |              |              |ab5l6nle      |              |hp57knle      |vgqs7n76      |              |              |
| 21|q4f7snez      |              |              |              |ab5l6nll      |              |hp57knll      |vgqs7n7d      |              |              |
| 22|q4f7sne6      |              |              |              |ab5l6nls      |              |hp57knls      |vgqs7n7k      |              |              |
| 23|q4f7sned      |              |              |              |ab5l6nlz      |              |              |vgqs7n7r      |              |              |
| 24|q4f7snek      |              |              |              |              |              |              |vgqs7n7y      |              |              |
| 25|q4f7sner      |              |              |              |              |              |              |vgqs7ne7      |              |              |
| 26|q4f7sney      |              |              |              |              |              |              |vgqs7nee      |              |              |
| 27|q4f7snl7      |              |              |              |              |              |              |vgqs7nel      |              |              |
| 28|              |              |              |              |              |              |              |vgqsenes      |              |              |
| 29|              |              |              |              |              |              |              |vgqsenez      |              |              |
| 2a|              |              |              |              |              |              |              |vgqsene6      |              |              |
| 2b|              |              |              |              |              |              |              |vgqsened      |              |              |
|400|              |jc47eu7e [8]  |p5qlsu7e [8]  |o097zuee [8]  |              |a5m7zu7e [8]  |              |              |              |              |
|401|              |jc47eu7l [8]  |p5qlsu7l [8]  |o097zuel [8]  |              |a5m7zu7l [8]  |              |              |              |              |
|402|              |jc47eu7s [8]  |p5qlsu7s [8]  |o097zues [8]  |              |a5m7zu7s [8]  |              |              |              |              |
|403|              |jc47eu7z [8]  |p5qlsu7z [8]  |o097zuez [8]  |              |a5m7zu7z [8]  |              |              |              |              |
|404|              |jc47eu76 [8]  |p5qlsu76 [8]  |o097zue6 [8]  |              |a5m7zu76 [8]  |              |              |              |              |
|405|              |jc47eu7d [8]  |p5qlsu7d [8]  |o097zued [8]  |              |a5m7zu7d [8]  |              |              |              |              |
|406|              |jc47eu7k [8]  |p5qlsu7k [8]  |o097zuek [8]  |              |a5m7zu7k [8]  |              |              |              |              |
|407|              |jc47eu7r [8]  |p5qlsu7r [8]  |o097zuer [8]  |              |a5m7zu7r [8]  |              |              |              |              |


| 20|2a00:1450:4001|2a00:1450:4007|2a00:1450:4008|2a00:1450:400e|2a00:1450:4016|
|---|--------------|--------------|--------------|--------------|--------------|
|   |FRA 法兰克福  |PAR 巴黎      |BER 柏林      |UNKNOWN       |MUC 慕尼黑    |
|  0|4g57knls      |              |              |              |h0j7sn7s      |
|  1|4g57knlz      |              |              |              |h0j7sn7z      |
|  2|4g57kn76      |              |cxg7en7z      |              |h0j7sn76      |
|  3|4g57kn7d      |              |cxg7en76      |              |h0j7sn7d      |
|  4|4g57knes      |              |cxg7en7d      |              |h0j7sn7y      |
|  5|4g57knez      |              |cxg7en7k      |              |h0j7sne7      |
|  6|4g57kne6      |              |cxg7ene7      |              |h0j7snee      |
|  7|4g57kned      |              |cxg7enee      |              |h0j7snel      |
|  8|4g57kn7e      |              |cxg7enel      |              |              |
|  9|4g57kn7l      |              |cxg7enes      |              |              |
|  a|4g57kn7s      |              |              |              |              |
|  b|4g57kn7z      |              |              |              |              |
|  c|4g57knks      |              |              |              |              |
|  d|              |              |              |              |              |
|  e|              |              |              |              |              |
|  f|              |              |              |              |              |
| 10|              |25ge7n7e      |              |              |              |
| 11|              |25ge7n7l      |              |              |              |
| 12|              |25ge7n7s      |              |              |              |
| 13|              |25ge7n7z      |              |              |              |
| 14|              |25ge7n76      |              |              |              |
| 15|              |25ge7n7d      |              |              |              |
| 16|4g57kndy      |25ge7n7k      |              |              |              |
| 17|              |25ge7n7r      |              |              |              |
| 18|              |25ge7nes      |              |              |              |
| 19|              |25ge7nez      |              |              |              |
| 1a|              |25ge7ne6      |              |              |              |
| 1b|              |25ge7ned      |              |              |              |
| 1c|4g57knek      |25ge7nek      |              |              |              |
| 1d|4g57kner      |25ge7ner      |              |              |              |
| 1e|4g57kney      |25ge7ney      |              |              |              |
| 1f|4g57knl7      |25ge7nl7      |              |              |              |
| 20|4g57knle      |              |              |              |              |
| 21|4g57knll      |              |              |              |              |
| 22|              |              |              |              |              |
| 2e|4g57knz6      |              |              |              |              |
| 3d|4g57knd7      |              |              |              |              |
| 42|4g57knke      |              |              |              |              |
| 400|4g57kuee[8]  |              |              |5hn7su7e [8]  |              |
| 401|4g57kuel[8]  |              |              |5hn7su7l [8]  |              |
| 402|4g57kues[8]  |              |              |5hn7su7s [8]  |              |
| 403|4g57kuez[8]  |              |              |5hn7su7z [8]  |              |
| 404|4g57kue6[8]  |              |              |5hn7su76 [8]  |              |
| 405|4g57kued[8]  |              |              |5hn7su7d [8]  |              |
| 406|4g57kuek[8]  |              |              |5hn7su7k [8]  |              |
| 407|4g57kuer[8]  |              |              |5hn7su7r [8]  |              |


5. SN 编码其他形式
------------------

    r?.sn-xxx-xxxx.googlevideo.com
    r?.sn-xxxx-xxxx.googlevideo.com
    r?.sn-xxxxxx-xxxx.googlevideo.com
    r?.sn-xxxxxxxx-xxxx.googlevideo.com
    r?.sn-xxxxxxxxx-xxxx.googlevideo.com
    r?.sn-xxxxxxxxxxxx-xxxx.googlevideo.com


[IATA 机场编码]:      http://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code
[服务器部署信息表格]: https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8
