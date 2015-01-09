[SN 编码]是 Youtube 视频缓存服务器域名中最常见的一种，编码为八位，含义未知。  
但是根据目前获取到的[地址列表]来看，相当有规律。

    r1---sn-[123][45][6][78].googlevideo.com

1. 前三位 `[123]` 代表城市，由 [IATA 机场编码]转换而来。参阅 [[1e100.net]] 的[服务器部署信息表格]。  
   转换规则：  
   下面的表格方框中，从左往右，从上到下依次对应 `a-y`，`z` 暂时未知。  
   注意左下角是 `0`，而不是 `1`。  
    
    ```
    | 6 d k r y |
    | --------- |
    | 5 c j q x |
    | 4 b i p w |
    | 3 a h o v |
    | 2 9 g n u |
    | 0 8 f m t |
    | --------- |
    |   7 e l s | z
    ```
    
    写成代码的形式：
    ```python
    #!/usr/bin/env python
    import sys
    table = '1023456789abcdefghijklmnopqrstuvwxyz'

    def iata2sn(iata):
        global table
        sn = ''
        for v in iata:
            i = ((ord(v) - ord('a')) * 7 + 5) % 36
            sn += table[i]
        return sn

    def sn2iata(sn):
        global table
        iata = ''
        for v in sn:
            i = table.index(v)
            i = (5 - i % 7) * 5 + i / 7 + 10
            iata += table[i]
        return iata

    def main():
        if len(sys.argv) != 3:
            print 'usage:\n\t./%s -i iata\n\t./%s -s sn'\
                % (sys.argv[0], sys.argv[0])
            sys.exit(1)

        if sys.argv[1] == '-i':
            print iata2sn(sys.argv[2])
        elif sys.argv[1] == '-s':
            print sn2iata(sys.argv[2])
        else:
            print 'Unknown option.'
            sys.exit(1)

    if __name__ == '__main__':
        main()
    ```

2. `[45]` 和 `[78]` 均为下表格中第一列 10 个字符的组合。  
    ```
      | 1 2 3 4 5 6
    7 | 8 9 a b c d
    e | f g h i j k
    l | m n o p q r
    s | t u v w x y
    z | 0 1 2 3 4 5
    6 | 7 8 9 a b c
    d | e f g h i j
    k | l m n o p q
    r | s t u v w x
    y | z
    ```
    
    例如：
    ```
       7e 7l 7s 7z 76 7d 7k 7r 7y
    e7 ee el es ez e6 ed ek er ey
    l7 le ll ls lz l6 ld lk lr ly
    s7 se    ss       sd sk sr
    ```
    
3. `[6]` 位 IPv6 地址为 `n` 或 `u`， IPv4 地址为 `m`。  

    例如：  
    * `a5mekn7r` 对应的 IPv6 地址段为 `2607:f8b0:4007:a::/64`，IPv4 地址段为 `74.125.103.0/24`。
    * `a5m7zu7r` 对应的 IPv6 地址段为 `2607:f8b0:4007:407::/64`，IPv4 地址段为 `74.125.215.0/24`。
    * `a5mekm76` 对应的 IPv4 地址段为 `208.117.242.0/24`，不支持 IPv6。  
    以上三种 sn 编码均属于洛杉矶。


[SN 编码]:            https://github.com/lennylxx/ipv6-hosts/wiki/YouTube#4-sn-%E7%BC%96%E7%A0%81%E5%9C%B0%E5%9D%80
[地址列表]:           https://docs.google.com/spreadsheets/d/14gT1GV1IE0oYCq-1Dy747_5FWNxL26R-9T5htJ485dY
[IATA 机场编码]:      https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code
[服务器部署信息表格]: https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8