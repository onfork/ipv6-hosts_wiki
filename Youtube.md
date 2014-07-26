### Youtube

####域名重定向地址
<pre>v?.lscache?.c.youtube.com
v?.nonxt?.c.youtube.com
tc.v?.cache?.c.youtube.com
v?.lscache?.googlevideo.com
v?.nonxt?.googlevideo.com
tc.v?.cache?.googlevideo.com
</pre>
经过实践，以上六种域名都是`bandaid-redirector.l.google.com`的aliase，由重定向服务器分配IP，地址不固定。  
但是所有地址在某一时间段内每次分配的IP都是同一个。  
每个域名有8组，每组域名24个，v1-v24。

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
IP段和IATA机场编码可参照[1e100.net服务器分布表格](https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8)。  
每组域名共20个，r1-r20。   

####SN编码地址
<pre>r?.sn-xxxxxxxx.c.youtube.com
r?.sn-xxxxxxxx.googlevideo.com
r?---sn-xxxxxxxx.c.youtube.com
r?---sn-xxxxxxxx.googlevideo.com</pre>
最近出现的新域名，xxxxxxxx为八位编码，含义未知，对应IP好像也不固定。  
每组域名共20个，r1-r20。 