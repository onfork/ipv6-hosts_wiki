> YouTube 域名规则

*.c.youtube.com 和 *.googlevideo.com 指向的地址是相同的。  
下文只列出 *.googlevideo.com。

1. 域名重定向地址
-----------------

    v?.lscache?.googlevideo.com
    v?.nonxt?.googlevideo.com
    tc.v?.cache?.googlevideo.com

经过实践，以上三种域名都是`bandaid-redirector.l.google.com`的aliase，
由重定向服务器分配IP，地址不固定。  
但是所有地址在某一时间段内分配的IP都是同一个。  
每种域名有8组，每组域名24个，v1-v24。

2. 固定地址
-----------

    v?.cache?.googlevideo.com

该域名指向的IP为固定IP。
目前已知的前缀均为**2a00:1450:400e::/48**，IPv6第4段取值范围400-407，
第8段取值范围10-17。
每组域名共8个，v1-v8。

3. 前缀限定地址
---------------

    r?.xxx??s??.googlevideo.com
    r?---xxx??s??.googlevideo.com

以上两种域名指向的IP相同，为固定IP，xxx([IATA 机场编码])决定服务器地理位置。  
IP段和IATA机场编码可参照 [[1e100.net]] 的[服务器部署信息表格]。  
每组域名共20个，r1-r20。   

4. SN 编码地址
--------------

    r?.sn-xxxxxxxx.googlevideo.com
    r?---sn-xxxxxxxx.googlevideo.com

最近出现的新域名，固定IP，xxxxxxxx为八位编码，[编码比较有规律](sn-domains)。   
每组域名共20个，r1-r20。对应的 IPv6 地址第8段取值范围则是0x6-0x19。  

> 此规则同样适用于 `*.c.docs.google.com` `*.gvt1.com` 和 `*.c.android.clients.google.com` 域名。

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

**下面是五个已知 sn 编码表格** [查看 Google Sheets 版本]  
  * 表头为 IPv6 前3段(48位)，第 1 列为 IPv6 第4段。
  * 左上角数字(20)代表每个编码域名的个数，中括号中数字为特别标明数量。
  * 表格第一行为 [IATA 机场编码]和城市名。
  * 上面的栗子可以在第一个表格的第7行找到。  

| 20|2001:4860:4001|2001:4860:4002|2001:4860:4006|2001:4860:4007|
|---|--------------|--------------|--------------|--------------|
|   |SJC/NUQ 圣何塞|DFW 达拉斯    |MIA 迈阿密    |LAX 洛杉矶    |
|  0|              |              |              |              |
|  1|nwj7kner      |              |              |              |
|  2|nwj7knee      |              |              |              |
|  3|nwj7knel      |              |              |              |
|  4|nwj7knes      |q4f7dn7r      |              |a5m7ln7s      |
|  5|nwj7knez      |q4f7dn7y      |              |a5m7ln7z      |
|  6|nwj7kne6      |q4f7dne7      |              |a5m7ln76      |
|  7|nwj7kned      |q4f7dnee      |              |a5m7ln7d      |
|  8|nwj7knek      |              |              |              |
|  9|              |q4f7dnel      |              |              |
|  a|              |q4f7dnes      |              |              |
|  b|              |q4f7dnez      |              |              |
|  c|              |q4f7dne6      |              |              |
|  d|o097zne7      |              |              |              |
|  e|o097znee      |              |              |              |
|  f|o097znel      |              |              |              |
| 10|o097znes      |              |              |              |
| 11|o097znez      |              |              |              |
| 12|o097zne6      |              |              |              |
| 13|o097zned      |              |              |              |
| 14|o097znek      |              |              |              |
|803|              |              |hp576n7s      |              |


| 12|2401:3800:4001|2401:3800:4002|
|---|--------------|--------------|
|   |PEK 北京      |SHA 上海      |
|  0|              |              |
|  1|              |ni57dn7e      |
|  2|2x37ln7e      |ni57dn7l      |
|  3|2x37ln7l      |              |
|  4|              |              |
|  5|2x37ln7s      |              |
|  6|2x37ln7z      |              |
|  7|2x37en7k      |              |


| 20|2404:6800:4001|2404:6800:4002|2404:6800:4003|2404:6800:4004|2404:6800:4005|2404:6800:4007|
|---|--------------|--------------|--------------|--------------|--------------|--------------|
|   |KUL 吉隆坡    |DEL 新德里    |SIN 新加坡    |NRT 东京千叶  |HKG 香港      |MAA 金奈      |
|  0|              |qxa7en7e      |npo7en7d      |              |i3b7rn7k [6]  |h557sn7r      |
|  1|              |qxa7en7l      |npo7en7k      |              |i3b7rn7r [6]  |h557sn7y      |
|  2|              |qxa7en7s      |npo7en7r      |              |i3b7rn7y [6]  |h557sne7      |
|  3|              |qxa7en7z      |npo7en7y      |              |i3b7rne7 [6]  |h557snee      |
|  4|30a7dn7e      |              |npo7ene7      |              |i3b7sn76      |h557snel      |
|  5|30a7dn7l      |              |npo7enee      |              |i3b7sn7d      |h557snes      |
|  6|30a7dn7s      |              |npo7enel      |              |i3b7sn7k      |h557snez      |
|  7|30a7dn7z      |              |npo7enes      |              |i3b7sn7r      |h557sne6      |
|  8|30a7en7s      |              |npo7zn7s [6]  |              |i3b7snek      |h557sned      |
|  9|30a7en76      |              |npo7zn7z [6]  |              |i3b7sner      |h557snek      |
|  a|              |              |              |              |i3b7sney      |              |
|  b|              |              |              |              |i3b7snl7      |              |
|  c|              |              |              |              |i3b7sn7e      |              |
|  d|              |              |              |              |i3b7sn7l      |              |
|  e|              |              |              |              |i3b7sn7s      |              |
|  f|              |              |              |              |i3b7sn7z      |              |
| 10|30a7en7z      |              |              |              |i3b7rnee [6]  |              |
| 11|30a7en7d      |              |              |              |i3b7rnel [6]  |              |
| 20|              |              |              |oguesn7l      |              |              |
| 21|              |              |              |oguesn7s      |              |              |
| 22|              |              |              |oguesn7z      |              |              |
| 23|              |              |              |oguesn76      |              |              |
| 24|              |              |              |oguesn7d      |              |              |
| 25|              |              |              |oguesn7k      |              |              |
| 26|              |              |              |oguesn7r      |              |              |
| 27|              |              |              |oguesn7y      |              |              |
| 28|              |              |              |oguesne7      |              |              |
| 29|              |              |              |oguesnee      |              |              |
| 2a|              |              |              |oguesnel      |              |              |
| 2b|              |              |              |oguesnes      |              |              |
| 2c|              |              |              |oguesnez      |              |              |
| 2d|              |              |              |oguesne6      |              |              |
| 2e|              |              |              |oguesned      |              |              |
| 2f|              |              |              |oguesnek      |              |              |
| 30|              |              |              |oguesney      |              |              |
| 31|              |              |              |oguesnl7      |              |              |
| 32|              |              |              |oguesnle      |              |              |
| 33|              |              |              |oguesnll      |              |              |
| 34|              |              |              |oguesnls      |              |              |
| 35|              |              |              |oguesnlz      |              |              |
| 36|              |              |              |oguesnl6      |              |              |
| 37|              |              |              |oguesnld      |              |              |
| 38|              |              |              |oguesnlk      |              |              |
| 39|              |              |              |oguesnlr      |              |              |
| 3a|              |              |              |oguesnly      |              |              |
| 3b|              |              |              |oguesns7      |              |              |
| 3c|              |              |              |oguesnse      |              |              |
| 3d|              |              |              |oguesnsl      |              |              |
| 3e|              |              |              |oguesnss      |              |              |
| 3f|              |              |              |oguesnsz      |              |              |


| 20|2607:f8b0:4000|2607:f8b0:4001|2607:f8b0:4004|2607:f8b0:4005|2607:f8b0:4006|2607:f8b0:4007|2607:f8b0:4008|2607:f8b0:4009|2607:f8b0:400a|2607:f8b0:400f|2607:f8b0:4012|
|---|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
|   |DFW 达拉斯    |CBF           |IAD 华盛顿    |NUQ/SJC 山景城|LGA 纽约      |LAX 洛杉矶    |MIA 迈阿密    |ORD 芝加哥    |SEA 西雅图    |DEN 丹佛      |QRO 克雷塔罗  |
|  0|q4f7dnsz      |              |p5qlsns6 [6]  |nwj7kney      |ab5l6nsy [6]  |a5mekn7d [6]  |              |vgqsen7e      |nx57ynee      |qxo7sn7e      |9gv7en7e      |
|  1|q4f7dns6      |              |p5qlsnsd [6]  |nwj7knl7      |              |a5mekn7k [6]  |              |vgqs7nes [6]  |nx57yn7s      |qxo7sn7l      |9gv7en7l      |
|  2|q4f7dner      |              |p5qlsnsk [6]  |o097znlk [6]  |ab5l6nl6      |a5m7znez      |hp57knlr [6]  |vgqs7nez [6]  |nx57yn7z      |qxo7sn7s      |9gv7en7s      |
|  3|q4f7dney      |              |p5qlsnsr [6]  |o097znlr [6]  |ab5l6nld      |a5m7zne6      |hp57knly [6]  |vgqs7ne6      |nx57yn76      |qxo7sn7z      |9gv7en7z      |
|  4|q4f7dnl7      |              |p5qlsnlk      |o097znl7      |ab5l6nss      |a5m7zned      |              |vgqs7ned      |nx57yn7d      |qxo7sn7k [6]  |9gv7en76      |
|  5|q4f7dnle      |              |p5qlsnlr      |o097znle      |ab5l6nsz      |a5m7znek      |              |vgqs7nek      |nx57yn7k      |qxo7sn7r [6]  |9gv7en7d      |
|  6|              |              |p5qlsnly      |o097znll      |ab5l6ns6      |a5m7zne7      |hp57kns7 [6]  |vgqs7ner      |nx57yn7r      |              |9gv7en7k      |
|  7|              |              |p5qlsns7      |o097znls      |              |a5m7znee      |hp57knse [6]  |vgqsenek [6]  |nx57yn7y      |              |9gv7en7r      |
|  8|              |              |p5qlsn7e      |              |ab5l6n7e      |a5m7znel      |              |vgqsener [6]  |nx57yne7      |              |9gv7ln7e      |
|  9|              |              |p5qlsn7l      |o097znl6      |ab5l6n7l      |a5m7znes      |              |vgqs7ney [6]  |nx57ynel      |              |9gv7ln7l      |
|  a|q4f7dnsd      |              |p5qlsn7s      |o097znld      |ab5l6nsd      |a5mekn7r [6]  |              |vgqsen7y      |nx57ynes      |              |9gv7ln7s      |
|  b|q4f7dnsk      |              |p5qlsn7z      |nwj7knls      |              |a5mekn7y [6]  |              |vgqsene7      |nx57ynez      |              |9gv7ln7z      |
|  c|q4f7dnzl      |              |p5qlsnsy [6]  |nwj7knlz      |ab5l6nsk [6]  |a5mekne7 [6]  |hp57kn7e [6]  |vgqsen7l      |nx57yney      |              |9gv7ln76      |
|  d|q4f7dnzs      |              |              |              |ab5l6nsr [6]  |a5meknee [6]  |hp57kn7l [6]  |vgqsen7s      |nx57ynl7      |              |9gv7ln7d      |
|  e|q4f7dnzz      |              |              |              |ab5l6n7s      |a5meknel [6]  |hp57kn7s [6]  |vgqsen7z      |nx57ynle      |              |9gv7ln7k      |
|  f|q4f7dnz6      |              |              |              |ab5l6n7z      |a5meknes [6]  |hp57kn7z [6]  |vgqsen76      |nx57ynll      |              |9gv7ln7r      |
| 10|              |              |p5qlsn7y      |              |ab5l6n76      |a5m7ln7k      |hp57kn76      |vgqs7nl7 [6]  |nx5e6n7s [6]  |              |              |
| 11|              |              |p5qlsne7      |              |ab5l6n7d      |a5m7ln7r      |hp57kn7d      |vgqseney [6]  |nx5e6n7z [6]  |              |              |
| 12|              |              |p5qlsnee      |              |ab5l6n7k      |a5m7ln7y      |hp57kn7k      |vgqsenl7 [6]  |nx5e6n76 [6]  |              |              |
| 13|              |              |p5qlsnel      |              |ab5l6n7r      |a5m7lne7      |hp57kn7r      |              |nx5e6n7d [6]  |              |              |
| 14|q4f7sn7e [6]  |              |p5qlsnes      |              |ab5l6n7y      |a5m7lnee      |hp57kn7y      |              |              |              |              |
| 15|q4f7sn7l [6]  |              |p5qlsnez      |              |ab5l6ne7      |a5m7lnel      |hp57kne7      |              |              |              |              |
| 16|q4f7sn7s [6]  |              |p5qlsne6      |              |ab5l6nee      |a5m7lnes      |hp57knee      |              |              |              |              |
| 17|q4f7sn7z [6]  |              |p5qlsned      |              |ab5l6nel      |a5m7lnez      |hp57knel      |vgqsen7d      |              |              |              |
| 18|q4f7sn76 [6]  |              |p5qlsney      |              |ab5l6nes      |a5m7lne6      |              |vgqsen7k      |              |              |              |
| 19|q4f7sn7d [6]  |              |p5qlsnl7      |              |ab5l6nez      |a5m7lned      |              |vgqsen7r      |              |              |              |
| 1a|q4f7sn7k [6]  |              |p5qlsnle      |              |ab5l6ne6      |a5m7lnek      |              |vgqsenee      |              |              |              |
| 1b|q4f7sn7r [6]  |              |p5qlsnll      |              |ab5l6ned      |a5m7lner      |              |vgqsenel      |              |              |              |
| 1c|q4f7sn7y      |              |p5qlsnse      |              |ab5l6nek      |              |              |vgqs7n7e      |              |              |              |
| 1d|q4f7sne7      |              |p5qlsnsl      |              |ab5l6ner      |              |              |vgqs7n7l      |              |              |              |
| 1e|q4f7snee      |              |p5qlsnss      |              |ab5l6ney      |              |              |vgqs7n7s      |              |              |              |
| 1f|q4f7snel      |              |p5qlsnsz      |              |ab5l6nl7      |              |              |vgqs7n7z      |              |              |              |
| 20|q4f7snes      |              |              |              |ab5l6nle      |              |hp57knle      |vgqs7n76      |              |              |              |
| 21|q4f7snez      |              |              |              |ab5l6nll      |              |hp57knll      |vgqs7n7d      |              |              |              |
| 22|q4f7sne6      |              |              |              |ab5l6nls      |              |hp57knls      |vgqs7n7k      |              |              |              |
| 23|q4f7sned      |              |              |              |ab5l6nlz      |              |              |vgqs7n7r      |              |              |              |
| 24|q4f7snek      |              |              |              |ab5l6nlk      |              |              |vgqs7n7y      |              |              |              |
| 25|q4f7sner      |              |              |              |ab5l6nlr      |              |              |vgqs7ne7      |              |              |              |
| 26|q4f7sney      |              |              |              |ab5l6nly      |              |              |vgqs7nee      |              |              |              |
| 27|q4f7snl7      |              |              |              |ab5l6ns7      |              |              |vgqs7nel      |              |              |              |
| 28|              |              |              |              |ab5l6nse      |              |              |vgqsenes      |              |              |              |
| 29|              |              |              |              |ab5l6nsl      |              |              |vgqsenez      |              |              |              |
| 2a|              |              |              |              |              |              |              |vgqsene6      |              |              |              |
| 2b|              |              |              |              |              |              |              |vgqsened      |              |              |              |
|400|              |jc47eu7e [8]  |p5qlsu7e [8]  |o097zuee [8]  |              |a5m7zu7e [8]  |              |              |              |              |              |
|401|              |jc47eu7l [8]  |p5qlsu7l [8]  |o097zuel [8]  |              |a5m7zu7l [8]  |              |              |              |              |              |
|402|              |jc47eu7s [8]  |p5qlsu7s [8]  |o097zues [8]  |              |a5m7zu7s [8]  |              |              |              |              |              |
|403|              |jc47eu7z [8]  |p5qlsu7z [8]  |o097zuez [8]  |              |a5m7zu7z [8]  |              |              |              |              |              |
|404|              |jc47eu76 [8]  |p5qlsu76 [8]  |o097zue6 [8]  |              |a5m7zu76 [8]  |              |              |              |              |              |
|405|              |jc47eu7d [8]  |p5qlsu7d [8]  |o097zued [8]  |              |a5m7zu7d [8]  |              |              |              |              |              |
|406|              |jc47eu7k [8]  |p5qlsu7k [8]  |o097zuek [8]  |              |a5m7zu7k [8]  |              |              |              |              |              |
|407|              |jc47eu7r [8]  |p5qlsu7r [8]  |o097zuer [8]  |              |a5m7zu7r [8]  |              |              |              |              |              |

| 20|2800:3f0:4002 |
|---|--------------|
|   |EZE 布宜诺斯艾利斯|
|  0|x1x7sn7k      |
|  1|x1x7sn7r      |
|  2|x1x7sn7y      |
|  3|x1x7sne7      |
|  4|x1x7snee      |
|  5|x1x7snel      |
|  6|x1x7snes      |
|  7|x1x7snez      |

| 20|2a00:1450:4001|2a00:1450:4007|2a00:1450:4008|2a00:1450:4009|2a00:1450:400b|2a00:1450:400e|2a00:1450:4016|2a00:1450:4017|
|---|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
|   |FRA 法兰克福  |PAR 巴黎      |BER 柏林      |LHR 伦敦      |DUB 都柏林    |AMS 阿姆斯特丹|MUC 慕尼黑    |SOF 索菲亚    |
|  0|4g57knls      |25ge7nls [6]  |              |aigllnze      |q0c7dn7e      |              |h0j7sn7s      |              |
|  1|4g57knlz      |25ge7nlz [6]  |              |aigllnzl      |q0c7dn7l      |              |h0j7sn7z      |nv47en7z      |
|  2|4g57kn76      |25ge7nl6 [6]  |cxg7en7z      |aigllnzs      |q0c7dn7s      |              |h0j7sn76      |nv47en76      |
|  3|4g57kn7d      |25ge7nld [6]  |cxg7en76      |aigllnzz      |q0c7dn7z      |              |h0j7sn7d      |nv47en7d      |
|  4|4g57knes      |              |cxg7en7d      |aiglln6k      |q0c7dn76      |5hn7snee      |h0j7sn7y      |nv47en7k      |
|  5|4g57knez      |              |cxg7en7k      |              |q0c7dn7d      |5hn7snel      |h0j7sne7      |nv47en7r      |
|  6|4g57kne6      |              |cxg7ene7      |aiglln6r      |q0c7dn7k      |5hn7snes      |h0j7snee      |nv47en7y      |
|  7|4g57kned      |              |cxg7enee      |aiglln6y      |q0c7dn7r      |5hn7snez      |h0j7snel      |nv47ene7      |
|  8|4g57kn7e      |25g7sn7z      |cxg7enel      |aigllnd7      |              |5hn7sne6      |              |nv47en7s      |
|  9|4g57kn7l      |25g7sn76      |cxg7enes      |              |              |5hn7sned      |              |nv47enes [6]  |
|  a|4g57kn7s      |25g7sn7d      |              |              |              |              |              |nv47enez [6]  |
|  b|4g57kn7z      |25g7sn7k      |              |              |              |              |              |nv47ene6 [6]  |
|  c|4g57knks      |25g7sn7r      |              |              |              |              |              |nv47ened [6]  |
|  d|4g57knkz      |25g7sn7y      |              |              |              |              |              |              |
|  e|4g57knk6      |25g7sne7      |              |              |              |              |              |              |
|  f|4g57knkd      |25g7snee      |              |              |              |              |              |              |
| 10|4g57kndk      |25ge7n7e      |              |              |              |5hn7snek      |              |              |
| 11|4g57kndr      |25ge7n7l      |              |              |              |5hn7sner      |              |              |
| 12|              |25ge7n7s      |              |              |              |5hn7sney      |              |              |
| 13|              |25ge7n7z      |              |              |              |5hn7snl7      |              |              |
| 14|              |25ge7n76      |              |              |              |5hn7snle      |              |              |
| 15|              |25ge7n7d      |              |              |              |5hn7snll      |              |              |
| 16|4g57kndy      |25ge7n7k      |              |              |              |5hn7snls      |              |              |
| 17|4g57knk7      |25ge7n7r      |              |              |              |5hn7snlz      |              |              |
| 18|              |25ge7nes      |              |              |              |5hn7snl6      |              |              |
| 19|              |25ge7nez      |              |              |              |5hn7snld      |              |              |
| 1a|              |25ge7ne6      |              |              |              |5hnezn7e      |              |              |
| 1b|              |25ge7ned      |              |              |              |5hnezn7l      |              |              |
| 1c|4g57knek      |25ge7nek      |              |aiglln7e      |              |5hnezn7s      |              |              |
| 1d|4g57kner      |25ge7ner      |              |aiglln7l      |              |5hnezn7z      |              |              |
| 1e|4g57kney      |25ge7ney      |              |aiglln7s      |              |5hnezn76      |              |              |
| 1f|4g57knl7      |25ge7nl7      |              |aiglln7z      |              |5hnezn7d      |              |              |
| 20|4g57knle      |              |              |aiglln76      |              |5hnezn7k      |              |              |
| 21|4g57knll      |              |              |aiglln7d      |              |5hnezn7r      |              |              |
| 22|4g57knl6      |              |              |aiglln7k      |              |5hnezn7y      |              |              |
| 23|4g57knld      |              |              |aiglln7r      |              |5hnezne7      |              |              |
| 24|4g57knsy      |              |              |aiglln7y      |              |5hneznee      |              |              |
| 25|4g57knz7      |              |              |aigllne7      |              |5hneznel      |              |              |
| 26|4g57knze      |              |              |aigllnee      |              |              |              |              |
| 27|4g57knzl      |              |              |aigllnel      |              |              |              |              |
| 28|              |              |              |aigllnes      |              |              |              |              |
| 29|              |              |              |aigllnez      |              |              |              |              |
| 2a|              |              |              |aigllne6      |              |              |              |              |
| 2b|              |              |              |aigllned      |              |              |              |              |
| 2c|4g57knzs      |              |              |aigllnek      |              |              |              |              |
| 2d|4g57knzz      |              |              |aigllner      |              |              |              |              |
| 2e|4g57knz6      |              |              |aigllney      |              |              |              |              |
| 2f|4g57knzd      |              |              |aigllnl7      |              |              |              |              |
| 30|4g57knzk      |              |              |aigllnle      |              |              |              |              |
| 31|4g57knzr      |              |              |aigllnll      |              |              |              |              |
| 32|4g57knzy      |              |              |aigllnls      |              |              |              |              |
| 33|4g57kn67      |              |              |aigllnlz      |              |              |              |              |
| 34|4g57kn6e      |              |              |aigllnl6      |              |              |              |              |
| 35|4g57kn6l      |              |              |aigllnld      |              |              |              |              |
| 36|4g57kn6s      |              |              |aigllnlk      |              |              |              |              |
| 37|4g57kn6z      |              |              |aigllnlr      |              |              |              |              |
| 38|4g57kn66      |              |              |aigllnly      |              |              |              |              |
| 39|4g57kn6d      |              |              |aigllns7      |              |              |              |              |
| 3a|4g57kn6k      |              |              |aigllnse      |              |              |              |              |
| 3b|4g57kn6r      |              |              |aigllnsl      |              |              |              |              |
| 3c|4g57kn6y      |              |              |aigllnss      |              |              |              |              |
| 3d|4g57knd7      |              |              |aigllnsz      |              |              |              |              |
| 3e|4g57knde      |              |              |aigllns6      |              |              |              |              |
| 3f|4g57kndl      |              |              |aigllnsd      |              |              |              |              |
| 40|4g57knd6      |              |              |aigllnsk      |              |              |              |              |
| 41|4g57kndd      |              |              |aigllnsr      |              |              |              |              |
| 42|4g57knke      |              |              |aigllnsy      |              |              |              |              |
| 43|4g57knkl      |              |              |aigllnz7      |              |              |              |              |
| 44|              |              |              |aigllnz6      |              |              |              |              |
| 45|              |              |              |aigllnzd      |              |              |              |              |
| 46|              |              |              |aigllnzk      |              |              |              |              |
| 47|              |              |              |aigllnzr      |              |              |              |              |
| 48|              |              |              |aigllnzy [6]  |              |              |              |              |
| 49|              |              |              |aiglln67 [6]  |              |              |              |              |
| 4a|              |              |              |aiglln6e [6]  |              |              |              |              |
| 4b|              |              |              |aiglln6l [6]  |              |              |              |              |
|400|4g57kuee [8]  |              |              |              |              |5hn7su7e [8]  |              |              |
|401|4g57kuel [8]  |              |              |              |              |5hn7su7l [8]  |              |              |
|402|4g57kues [8]  |              |              |              |              |5hn7su7s [8]  |              |              |
|403|4g57kuez [8]  |              |              |              |              |5hn7su7z [8]  |              |              |
|404|4g57kue6 [8]  |              |              |              |              |5hn7su76 [8]  |              |              |
|405|4g57kued [8]  |              |              |              |              |5hn7su7d [8]  |              |              |
|406|4g57kuek [8]  |              |              |              |              |5hn7su7k [8]  |              |              |
|407|4g57kuer [8]  |              |              |              |              |5hn7su7r [8]  |              |              |


5. SN 编码其他形式
------------------

    r?.sn-xxx-xxxx.googlevideo.com
    r?.sn-xxxx-xxxx.googlevideo.com
    r?.sn-xxxxxx-xxxx.googlevideo.com
    r?.sn-xxxxxxxx-xxxx.googlevideo.com
    r?.sn-xxxxxxxxx-xxxx.googlevideo.com
    r?.sn-xxxxxxxxxxxx-xxxx.googlevideo.com


[IATA 机场编码]:           http://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code
[服务器部署信息表格]:      https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8
[查看 Google Sheets 版本]: https://docs.google.com/spreadsheets/d/14gT1GV1IE0oYCq-1Dy747_5FWNxL26R-9T5htJ485dY