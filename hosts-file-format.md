Hosts file is a plain text file, it's used to combine the IPs to corresponding domains.  
According to http://linux.die.net/man/5/hosts, here are the rules of hosts file.

1. Only one IP address in each line.
2. Format in one line,
   <pre>\<ip-address\> \<hostname\> [aliases...]</pre>
   These items are separated by one or more `Space` or `Tab`.
3. `hostname` can only contain `alphabet`, `number`, `hyphen(-)` and `dot(.)`. It must begin with alphanumeric and end with alphanumeric.
4. `alias` is optional, can be many.
5. The content that begins `hash(#)` ends with line break is regarded as comment.
6. Empty lines are ignored.

So, we can know that:

1. hosts file doesn't support wildcard and regex expression.  
   `123.123.123.123 *.mydomain.com`  
   Lines like this is illegal.
2. Comments can be placed at the end of line.  
   `123.123.123.123 foo.mydomain.com #comments`