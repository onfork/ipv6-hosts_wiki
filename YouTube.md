> YouTube 域名规则

*.c.youtube.com 和 *.googlevideo.com 指向的地址是相同的。

1. 域名重定向地址
----
<pre>v?.lscache?.c.youtube.com
v?.nonxt?.c.youtube.com
tc.v?.cache?.c.youtube.com
v?.lscache?.googlevideo.com
v?.nonxt?.googlevideo.com
tc.v?.cache?.googlevideo.com
</pre>
经过实践，以上六种域名都是`bandaid-redirector.l.google.com`的aliase，由重定向服务器分配IP，地址不固定。  
但是所有地址在某一时间段内分配的IP都是同一个。  
每种域名有8组，每组域名24个，v1-v24。

2. 固定地址
----
<pre>v?.cache?.c.youtube.com
v?.cache?.googlevideo.com</pre>
以上两种域名指向的IP相同，为固定IP。
目前已知的前缀均为**2a00:1450:400e::/48**，IPv6第4段取值范围400-407，第8段取值范围10-17。
每组域名共8个，v1-v8。

3. 前缀限定地址
----
<pre>r?.xxx??s??.c.youtube.com
r?.xxx??s??.googlevideo.com
r?---xxx??s??.c.youtube.com
r?---xxx??s??.googlevideo.com</pre>
以上四种域名指向的IP相同，为固定IP，xxx(IATA机场编码)决定服务器地理位置。  
IP段和IATA机场编码可参照[[1e100.net]]的[服务器部署信息表格](https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8)。  
每组域名共20个，r1-r20。   

4. SN编码地址
----
<pre>r?.sn-xxxxxxxx.c.youtube.com
r?.sn-xxxxxxxx.googlevideo.com
r?---sn-xxxxxxxx.c.youtube.com
r?---sn-xxxxxxxx.googlevideo.com</pre>
最近出现的新域名，固定IP，xxxxxxxx为八位编码，含义未知，但编码比较有规律。  
每组域名共20个，r1-r20。对应的IPv6地址第8段取值范围则是0x6-0x19。  

**栗子**
<pre>2001:4860:4001:7::6 r1---sn-nwj7kned.googlevideo.com
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
2001:4860:4001:7::19 r20---sn-nwj7kned.googlevideo.com</pre>  

**下面是三个已知sn编码表格(表格第一列为IPv6第4段)**  
(上面的栗子可以在第三个表格的第7行找到)  

||2607:f8b0:4004|2607:f8b0:4005|2607:f8b0:4006|2607:f8b0:4007|2607:f8b0:4009|
|---|---|---|---|---|---|
|1||nwj7knl7|||vgqs7nes|
|2|||ab5l6nl6||vgqs7nez|
|3|||||vgqs7ne6|
|4|||||vgqs7ned|
|5|||||vgqs7nek|
|6|||||vgqs7ner|
|10||||a5m7ln7k|
|11||||a5m7ln7r|
|12||||a5m7ln7y|
|13||||a5m7lne7|
|14||||a5m7lnee|
|15|||ab5l6ne7|a5m7lnel|
|16|||ab5l6nee|a5m7lnes|
|17|||ab5l6nel|a5m7lnez|
|18|p5qlsney||ab5l6nes|a5m7lne6|
|19|p5qlsnl7||ab5l6nez|a5m7lned|
|1a|p5qlsnle||ab5l6ne6|a5m7lnek|
|1b|p5qlsnll||ab5l6ned|a5m7lner|
|1c|||ab5l6nek||vgqs7n7e|
|1d|||||vgqs7n7l|
|1e|||||vgqs7n7s|
|1f|||ab5l6nl7||vgqs7n7z|
|20|||ab5l6nle||vgqs7n76|
|21|||ab5l6nll||vgqs7n7d|
|22|||ab5l6nls||vgqs7n7k|
|23|||ab5l6nlz||vgqs7n7r|
|24|||||vgqs7n7y|
|25|||||vgqs7ne7|
|26|||||vgqs7nee|
|27|||||vgqs7nel|
|400||o097zuee||a5m7zu7e||
|401||o097zuel||a5m7zu7l||
|402||o097zues||a5m7zu7s||
|403||o097zuez||a5m7zu7z||
|404||o097zue6||a5m7zu76||
|405||o097zued||a5m7zu7d||
|406||o097zuek||a5m7zu7k||
|407||o097zuer||a5m7zu7r||


||2404:6800:4002|2404:6800:4003|2404:6800:4005|2404:6800:4007|
|---|---|---|---|---|
|0|qxa7en7e|npo7en7d||h557sn7r|
|1|qxa7en7l|npo7en7k||h557sn7y|
|2|qxa7en7s|npo7en7r||h557sne7|
|3|qxa7en7z|npo7en7y||h557snee|
|4|||i3b7sn76|h557snel|
|5|||i3b7sn7d|h557snes|
|6|||i3b7sn7k|h557snez|
|7|||i3b7sn7r|h557sne6|
|8||||h557sned|
|9||||h557snek|
|c|||i3b7sn7e||
|d|||i3b7sn7l||
|e|||i3b7sn7s||
|f|||i3b7sn7z||

||2001:4860:4001|2001:4860:4007|
|---|---|---|
|1|nwj7kner|
|2|nwj7knee|
|3|nwj7knel|
|4|nwj7knes|a5m7ln7s|
|5|nwj7knez|a5m7ln7z|
|6|nwj7kne6|a5m7ln76|
|7|nwj7kned|a5m7ln7d|
|8|nwj7knek|
|d|o097zne7|
|e|o097znee|
|f|o097znel|
|10|o097znes|a5m7ln7k|
|11|o097znez|a5m7ln7r|
|12|o097zne6|a5m7ln7y|
|13|o097zned|
|14|o097znek|


5. 其他形式
----
<pre>r?.sn-xxxx-xxxx.googlevideo.com
r?.sn-xxxxxx-xxxx.googlevideo.com
r?.sn-xxxxxxxx-xxxx.googlevideo.com
r?.sn-xxxxxxxxx-xxxx.googlevideo.com
r?.sn-xxxxxxxxxxxx-xxxx.googlevideo.com</pre>