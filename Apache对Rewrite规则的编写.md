
Rewrite 规则可以对来访问的主机实现控制

```apache
<VirtualHost *:81>
   RewriteEngine On 
   RewriteRule ^(.*) http://www.baidu.com [L]
   DocumentRoot "/web/ceshi"
   <Directory "/web/ceshi">
       Options Indexes MultiViews FollowSymLinks
       AllowOverride All
       Order allow,deny
       Allow from all
   </Directory>
</VirtualHost>
```
