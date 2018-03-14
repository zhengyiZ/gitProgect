## NGINX 学习
@(技能提升)[nginx, location]

***注意: 原始编辑文档中,美元符号前面的斜杠是markdown语法的转义符,否则会被解析为公式***

1. loaaction 区分大小写的匹配方式:
>A regular expression is preceded with the tilde (~) for **`case-sensitive`**  matching, or the tilde-asterisk (~*) for  **`case-insensitive`** matching. The following example matches URIs that include the string .html or .htm in any position.
>>以下表示区分大小写的匹配方式:
location ~ \.html? {
    ...
}

2. 重写请求的 URI,  重写后重新与location 做匹配(相当于请求的转发)
Rewriting URIs in Requests
>A request URI can be modified multiple times during request processing through the use of the rewrite directive, which has one optional and two required parameters. The first (required) parameter is the regular expression that the request URI must match. The second parameter is the URI to substitute for the matching URI. The optional third parameter is a flag that can halt processing of further rewrite directives or send a redirect (code 301 or 302). For example:
>>例子: 127.0.0.1/users/zhangsan --> 127.0.0.1/show?user=zhangsan
location /users/ {
    rewrite  ^/users/(.*)\$          /show?user=\$1             break;  
}

>There are two parameters that interrupt processing of rewrite directives:
-  **last** – Stops execution of the rewrite directives in the current server or location context, but NGINX Plus searches for locations that match the rewritten URI, and any rewrite directives in the new location are applied (meaning the URI can be changed again).
- **break** – Like the break directive, stops processing of rewrite directives in the current context and cancels the search for locations that match the new URI. The rewrite directives in the new location are not executed.



添加一些消息.

添加一行内容;







更多nginx location 的配置方式:见: [nginx-web-server](https://www.nginx.com/resources/admin-guide/nginx-web-server/)

