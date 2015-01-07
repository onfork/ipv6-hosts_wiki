[SN 编码]是 Youtube 视频缓存服务器域名中最常见的一种，编码为八位，含义未知。  
但是根据目前获取到的[地址列表]来看，相当有规律，猜测是做了 hash。

    r1---sn-[123][45][6][78].googlevideo.com

1. 前三位 `[123]` 含义未知，猜测应该是代表某个城市。

2. `[45]` 和 `[78]` 均为下表格中第一列除 0 外的 10 个字符的组合。  

   例如：  

           7e 7l 7s 7z 76 7d 7k 7r 7y
        e7 ee el es ez e6 ed ek er ey
        l7 le ll ls lz l6 ld lk lr ly
        s7 se    ss       sd sk sr

3. `[6]` 位 IPv6 地址为 `n`， IPv4 地址为 `m`。  

   例如：  
   `a5mekn7r` 对应的 IPv6 地址段为 `2607:f8b0:4007:a::/64`，IPv4 地址段为 `74.125.103.0/24`。  
   `a5mekm76` 对应的 IPv4 地址段为 `208.117.242.0/24`，不支持 IPv6。


**表格**

    0 1 2 3 4 5 6
    7 8 9 a b c d
    e f g h i j k
    l m n o p q r
    s t u v w x y 
    z 0 1 2 3 4 5
    6 7 8 9 a b c
    d e f g h i j
    k l m n o p q
    r s t u v w x
    y z


[SN 编码]:   https://github.com/lennylxx/ipv6-hosts/wiki/YouTube#4-sn-%E7%BC%96%E7%A0%81%E5%9C%B0%E5%9D%80
[地址列表]:  https://docs.google.com/spreadsheets/d/14gT1GV1IE0oYCq-1Dy747_5FWNxL26R-9T5htJ485dY