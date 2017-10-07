> This page explains the encoding method of SN domains that have 8 characters.  
> Other form please refer to [[GGC]].

[SN domains] are widely used in YouTube video cache servers.
There are 8 significant characters which represent the servers' geographic
location and serial number of server groups.

According to the [domain list] collected so far, the pattern is similar to
[[1e100.net]].

**Pattern**

    r1---sn-[123][45][6][78].googlevideo.com

**Example**

    r1---sn-a5mekn7r.googlevideo.com

1. `[123]` represents city name, it's converted from [IATA airport code].
   Read more at [1e100.net servers deployment geoinfo].

   **Conversion rules**  
   * The 25 chars in the following box represent `a-y` respectively from left
     to right, top to bottom, i.e, `5` is for `a`, `t` is for `y`.
   * Note that the char in the bottom left corner is `0`, not `1`.
   * Besides, `1` is for `z`.

   It's a form of [Substitution Cipher], the tableau can be get by 90 degree counter-clockwise rotation of alphanumeric table.

   According to the rules, `a5m` in the example above can be reverse converted
   to `lax`, it's Los Angeles.

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
    
    Writing in code:
    ```python
    table = '1023456789abcdefghijklmnopqrstuvwxyz'
    def iata2sn(iata):
        global table
        sn = ''
        for v in iata:
            i = ((ord(v) - ord('a')) * 7 + 5) % 36
            sn += table[i]
        return sn
    ```

    Reverse conversion:
    ```python
    table = '1023456789abcdefghijklmnopqrstuvwxyz'
    def sn2iata(sn):
        global table
        iata = ''
        for v in sn:
            i = table.index(v)
            i = (5 - i % 7) * 5 + i / 7 + 10
            iata += table[i]
        return iata
    ```

2. `[45]` and `[78]` are combinations of first column's 10 chars in the table
    below. They represent the servers' group (Point of Presence) numbers. It's `0-9` from top to
    bottom respectively.

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
    So, `ek` and `7r` in the example can be reverse converted to `17` and `08`.

    `00`-`39`:
    ```
       7e 7l 7s 7z 76 7d 7k 7r 7y
    e7 ee el es ez e6 ed ek er ey
    l7 le ll ls lz l6 ld lk lr ly
    s7 se sl ss sz    sd sk sr
    ```
    `7e` represents `01`, `el` is for `12`, `s7` is for `30`, etc.

    Writing in code:
    ```python
    table = '1023456789abcdefghijklmnopqrstuvwxyz'
    def num2code(num):
        global table
        code = ''
        for v in num:
            i = ((ord(v) - ord('0') + 1) * 7) % 36
            code += table[i]
        return code
    ```

3. `[6]` in the SN domain is `n` or `u` for IPv6, it's `m` for IPv4.

    The range of `49-64` bits in `n`'s corresponding IPv6 addresses is `0 - 3ff`.  
    The range of `49-64` bits in `u`'s corresponding IPv6 addresses is `400 - 7ff`.  
    (Read more about the IPv6 address allocation rules at [[Google]].)

    e.g. 
    * `a5mekn7r`, IPv6 prefix is `2607:f8b0:4007:a::/64`,
                  IPv4 prefix is`74.125.103.0/24`.
    * `a5m7zu7r`, IPv6 prefix is `2607:f8b0:4007:407::/64`,
                  IPv4 prefix is `74.125.215.0/24`.
    * `a5mekm76`, no IPv6, IPv4 prefix is `208.117.242.0/24`.  

    `a5m` can be reverse converted to `lax`, so all of three SN domains above
     belong to Los Angeles.


* We can convert `lax17s08` of 1e100.net style to `a5mekn7r` of SN domains style.
* See [conversion code].
* See all [SN domains].

[SN domains]: https://github.com/lennylxx/ipv6-hosts/wiki/YouTube#4-sn-%E7%BC%96%E7%A0%81%E5%9C%B0%E5%9D%80
[domain list]: https://docs.google.com/spreadsheets/d/14gT1GV1IE0oYCq-1Dy747_5FWNxL26R-9T5htJ485dY
[IATA airport code]: https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code
[1e100.net servers deployment geoinfo]: https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8
[Substitution Cipher]: https://en.wikipedia.org/wiki/Substitution_cipher
[conversion code]: https://github.com/lennylxx/ipv6-hosts/blob/master/tools/conv.py
