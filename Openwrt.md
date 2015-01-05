在 Openwrt 上使用 ipv6-hosts 文件

1. 复制 hosts 文件到 /etc/hosts
2. 修改文件权限
   <pre># chmod 644 /etc/hosts</pre>
3. 修改 dnsmasq 配置文件 `/etc/config/dhcp`   
<pre>config dnsmasq
        option domainneeded '1'
        option bogusnxdomain '1'
        option boguspriv '1'
        option localise_queries '1'
        option rebind_protection '1'
        option local '/lan/'
        option domain 'lan'
        option expandhosts '1'
        option authoritative '1'
        option readethers '1'
        option leasefile '/tmp/dhcp.leases'
        option resolvfile '/tmp/resolv.conf.auto'</pre>
4. 重启 dnsmasq  
<pre># /etc/init.d/dnsmasq restart</pre>

===

测试  
<pre>dig @192.168.1.1 www.google.com aaaa</pre>
