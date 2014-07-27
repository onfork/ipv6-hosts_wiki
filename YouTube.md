> YouTube 域名规则

####域名重定向地址
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

####固定地址
<pre>v?.cache?.c.youtube.com
v?.cache?.googlevideo.com</pre>
以上两种域名指向的IP相同，为固定IP。
目前已知的前缀均为**2a00:1450:400e::/48**，IPv6第4段取值范围400-407，第8段取值范围10-17。
每组域名共8个，v1-v8。

####前缀限定地址
<pre>r?.xxx??s??.c.youtube.com
r?.xxx??s??.googlevideo.com
r?---xxx??s??.c.youtube.com
r?---xxx??s??.googlevideo.com</pre>
以上四种域名指向的IP相同，为固定IP，xxx(IATA机场编码)决定服务器地理位置。  
IP段和IATA机场编码可参照[1e100.net](https://github.com/lennylxx/ipv6-hosts/wiki/1e100.net)的[服务器部署信息表格](https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8)。  
每组域名共20个，r1-r20。   

####SN编码地址
<pre>r?.sn-xxxxxxxx.c.youtube.com
r?.sn-xxxxxxxx.googlevideo.com
r?---sn-xxxxxxxx.c.youtube.com
r?---sn-xxxxxxxx.googlevideo.com</pre>
最近出现的新域名，固定IP，xxxxxxxx为八位编码，含义未知，但编码比较有规律。  
每组域名共20个，r1-r20。 

**下面是三个已知sn编码表格(表格第一列为IPv6第4段)**  

||2607:f8b0:4005|2607:f8b0:4007|2607:f8b0:4009|
|---|---|---|---|
|1|nwj7knl7||vgqs7nes|
|2|||vgqs7nez|
|3|||vgqs7ne6|
|4|||vgqs7ned|
|5|||vgqs7nek|
|11||a5m7ln7r|
|12||a5m7ln7y|
|13||a5m7lne7|
|14||a5m7lnee|
|15||a5m7lnel|
|16||a5m7lnes|
|17||a5m7lnez|
|18||a5m7lne6|
|19||a5m7lned|
|1a||a5m7lnek|
|1c|||vgqs7n7e|
|1d|||vgqs7n7l|
|1e|||vgqs7n7s|
|1f|||vgqs7n7z|
|20|||vgqs7n76|
|21|||vgqs7n7d|
|22|||vgqs7n7k|
|23|||vgqs7n7r|
|24|||vgqs7n7y|
|25|||vgqs7ne7|
|26|||vgqs7nee|
|27|||vgqs7nel|


||2404:6800:4002|2404:6800:4003|2404:6800:4007|
|---|---|---|---|
|0|qxa7en7e|npo7en7d|h557sn7r|
|1|qxa7en7l|npo7en7k|h557sn7y|
|2|qxa7en7s|npo7en7r|h557sne7|
|3|qxa7en7z|npo7en7y|h557snee|
|4|||h557snel|
|5|||h557snes|
|6|||h557snez|
|7|||h557sne6|
|8|||h557sned|
|9|||h557snek|

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
|10|o097znes|
|11|o097znez|
|12|o097zne6|
|13|o097zned|
|14|o097znek|