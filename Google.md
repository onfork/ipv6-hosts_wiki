Google 有着自己的内容分发网络(CDN)，按照其[官网]的说法：
> Google 有一个可以供全球超过 100 多个国家访问的多层内容分发平台。这个平台构成了 Google 全球网络的基础设施，其将[数据中心]和骨干网络与边缘接入点(入网点)连接了起来。通过这个内容分发平台，可以以尽可能高的性能和较低的费用，将 Google 的内容和服务提供给网络运营商们，从而为用户提供服务。

> 原始内容以副本的形式存放在 Google 数据中心中，目的是增加冗余，针对不同的终端用户提供高效率的服务，通过 Google 骨干网分发给用户。

> Google Global Cache (GGC) 是这个内容分发平台的最后一层，最接近用户。网络运营商和 ISP 可以通过 GGC 将少量 Google 服务器部署在他们自己的网络中，从而提供 Google 内容。Google 的流量管理系统可以将用户引导至针对用户来说性能最好的节点。

===

Google ([[AS15169]]) IPv6 地址分配：
```
2001:4860:4000::/36	United States
2404:6800:4000::/36	Australia
2607:f8b0:4000::/36	United States
2800:03f0:4000::/36	Argentina
2a00:1450:4000::/36	Ireland
2c0f:fb50:4000::/36	Kenya
```

Google IP 段的管理方式：  
以 `2607:f8b0:4000::/36` 为例。  
掩码有 36 位，因此理论上，这个 IP 段可用地址数为 2 ^ 92，约 4.95e27 个。

1. 第 `33-48` 位 (共 16 位) 表示城市编号，如 `4000` 代表达拉斯，`4007` 代表洛杉矶，`400a` 代表西雅图等等。  
   (需要注意的是，由于 Google 所有的 IP 段都有 36 位掩码，因此所有的城市编号都是以 `4` 开头的。)
2. 第 `49-64` 位 (共 16 位) 则分成 5 段，每段使用方式不同，具体见下表格。

    | 49-64 位  | 用途           |
    | --------- | -------------- |
    | 0-3ff     | sn [20]/[6]    |
    | 400-7ff   | sn [8]         |
    | 800-bff   | iata 1e100.net |
    | c00-fff   | xx   1e100.net |
    | remaining | unknown        |

    如表格所示：  
    * `0-3ff` 地址段用于 **sn 编码域名**，每组地址 20 个或 6 个。  
      如在 `4007` 洛杉矶(LAX)，`1b` 对应编码 `a5m7lner`。  
      (域可以是`*.googlevideo.com` `*.gvt1.com` `*.c.youtube.com``*.c.docs.google.com` `*.c.android.clients.google.com`等。)
    * `400-3ff` 地址段也用于 **sn 编码域名**，每组地址则为 8 个。同上。  
      如在洛杉矶，`402` 对应编码 `a5m7zu7s`。
    * `800-bff` 地址段用于 **1e100.net 域名**的 [IATA 编码]地址，每组地址 32 个。  
      映射到普通 Google 服务域名，如 `*.google.com` `*.appspot.com` `*.blogspot.com` `*.ggpht.com.com` `*.gstatic.com`等。  
      如在 `4002` 亚特兰大(ATL)，`802` 对应编码 `atl14s08`。
    * `c00-fff` 地址段用于 **1e100.net 域名**的两位字母编码地址，每组地址 256 个。同上。  
      如在亚特兰大，`c01` 对应编码 `yh`。

    sn 编码域名和 1e100.net 域名的详细信息参见维基页面 [sn 编码域名](sn-domains)、[[YouTube]] 和 [[1e100.net]]。

3. 第 `65-112` 位 (共 48 位) 均为 0。
4. 第 `113-128` 位 (共 16 位) 表示服务器编号，对应独立二级域名，具体规则请查看 hosts 文件。


[官网]:         https://peering.google.com/about/ggc.html
[数据中心]:     https://www.google.com/about/datacenters
[IATA 编码]:    https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code