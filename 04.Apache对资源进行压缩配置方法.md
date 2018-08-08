如何在apache中开启gzip压缩服务

apache服务器设置gzip压缩是web开发当中很普遍的做法. 假设你要请求一个100k的文件, 网络传输速度为50k/s, 需要2s才能得到数据, 但是如果在服务器端设置了gzip压缩, 将文件压缩到了50k(实际上的压缩率往往小于50%), 这时候只需1s就能得到数据, 然后在客户端解压即可

![image](pic/1.png)

需要配置如下打开apache的httpd.conf配置文件, 首先要确保要加载如下配置

```shell
[root@zhangyz ~]# vim /etc/httpd/conf/httpd.conf
LoadModule deflate_module modules/mod_deflate.so

<IfModule mod_deflate.c>
    # 告诉apache对传输到浏览器的内容进行压缩
    SetOutputFilter DEFLATE
    # 压缩等级9
    DeflateCompressionLevel 9
</IfModule>
```

之后, 重新启动apache服务

```shell
[root@zhangyz ~]# service httpd restart
```

以上是对所有的文件进行gzip压缩. 压缩等级是1-9之间的整数, 取值范围在1(最低)到9(最高)之间, 不建议设置太高, 虽然有很高的压缩率, 但是占用更多的CPU资源.

实际开发中我们并不需要对所有文件进行压缩, 比如我们无需对图片文件进行gzip压缩, 因为图片文件(一般为jpg, png, pdf, mp3等格式)本身已经被压缩过了, 在进行gzip压缩可能会适得其反

比如我们要对图片等特殊文件不进行gzip压缩处理

```shell
<IfModule mod_deflate.c>
    # 告诉apache对传输到浏览器的内容进行压缩
    SetOutputFilter DEFLATE
    # 压缩等级9
    DeflateCompressionLevel 9
    # 设置不对后缀 gif, jpg, jpeg, png的图片文件进行压缩
    SetEnvIfNoCase Request_URI .(?:gif|jpe?g|png)$ no-gzip dont-vary
</IfModule>
```

或者指定文件格式进行压缩

```shell
<IfModule mod_deflate.c>
    # 压缩等级9
    DeflateCompressionLevel 9
    # 压缩类型 html, xml, php, css, js
    AddOutputFilterByType DEFLATE text/html text/plain  text/xml application/x-javascript application/x-httpd-php
    AddOutputFilter DEFLATE js css
</IfModule>
```

修改好后, 保存httpd.conf文件, 记得重启 apache, 在刷新浏览器看请求, 应该就生效了
```shell
<IfModule mod_deflate.c>
    SetOutputFilter DEFLATE
    DeflateCompressionLevel 9
    AddOutputFilter DEFLATE
    AddOutputFilterByType DEFLATE text/html text/plain text/xml application/x-JavaScript application/x-httpd-php
    AddOutputFilter DEFLATE js css
</IfModule>
```
