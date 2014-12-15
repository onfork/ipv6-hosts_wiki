hosts 文件是一个纯文本文件，用于将 IP 地址和域名关联起来。  
根据 http://linux.die.net/man/5/hosts 的描述，hosts 文件的格式如下：

1. 每行一个IP地址。
2. 每行的格式：
   <pre>\<ip-address\> \<hostname\> [aliases...]</pre>
   三项以任意数量的空格符(Space)或者制表符(Tab)隔开。
3. 主机名(hostname)只能包含 字母、数字、减号(-)和句号(.)；并且必须以字母数字开头，以字母数字结尾。
4. 别名(alias)可选，可以是多个。
5. 井号(#)开头，直到行尾的文本被视为注释内容。
6. 空行被忽略。

因此，我们可以得知：

1. hosts文件不支持通配符(wildcard)和正则表达式(regex expression)：   
   `123.123.123.123 *.mydomain.com`  
   类似这样的条目是不合法的。
2. 注释可以放在行尾：  
   `123.123.123.123 foo.mydomain.com #comments`