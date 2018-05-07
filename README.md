#### Apache的编译安装方法

```shell
[root@zhangyz httpd-2.2.15]# ./configure --prefix=/usr/local/apache \
--sysconfdir=/etc/httpd/ \
--enable-modules=all \
--enable-mods-shared=all \
--enable-so \
--enable-ssl \
--enable-cgi \
--enable-rewrite \
--with-apr=/usr/local/apr \
--with-apr-util=/usr/local/apr-util/ \
--with-pcre \
--with-libxml2 \
--with-mpm=event \
--enable-mpms-shared=all
```

#### 常用编译参数一览

```shell
./configure //配置源代码树

--prefix=/usr/local/apache2 //体系无关文件的顶级安装目录PREFIX ，也就Apache的安装目录。

--sysconfdir=/etc/httpd/ 配置文件路径

--enable-module=so //打开 so 模块，so 模块是用来提 DSO 支持的 apache 核心模块

--enable-deflate=shared //支持网页压缩

--enable-expires=shared //支持 HTTP 控制

--enable-rewrite=shared //支持 URL 重写

--enable-cache //支持缓存

--enable-file-cache //支持文件缓存

--enable-mem-cache //支持记忆缓存

--enable-disk-cache //支持磁盘缓存

--enable-static-support //支持静态连接(默认为动态连接)

--enable-static-htpasswd //使用静态连接编译 htpasswd – 管理用于基本认证的用户文件

--enable-static-htdigest //使用静态连接编译 htdigest – 管理用于摘要认证的用户文件

--enable-static-rotatelogs //使用静态连接编译 rotatelogs – 滚动 Apache 日志的管道日志程序

--enable-static-logresolve //使用静态连接编译 logresolve – 解析 Apache 日志中的IP地址为主机名

--enable-static-htdbm //使用静态连接编译 htdbm – 操作 DBM 密码数据库

--enable-static-ab //使用静态连接编译 ab – Apache HTTP 服务器性能测试工具

--enable-static-checkgid //使用静态连接编译 checkgid

--disable-cgid //禁止用一个外部 CGI 守护进程执行CGI脚本

--disable-cgi //禁止编译 CGI 版本的 PHP

--disable-userdir //禁止用户从自己的主目录中提供页面

--with-mpm=worker // 让apache以worker方式运行

--enable-authn-dbm=shared // 对动态数据库进行操作。Rewrite时需要。以下是分门别类的更多参数注解，与上面的会有重复用于apr的configure脚本的选项：可选特性

--enable-experimental-libtool 启用试验性质的自定义libtool

--disable-libtool-lock 取消锁定(可能导致并行编译崩溃)

--enable-debug 启用调试编译，仅供开发人员使用。

--enable-maintainer-mode 打开调试和编译时警告，仅供开发人员使用。

--enable-profile 打开编译profiling(GCC)

--enable-pool-debug[=yes|no|verbose|verbose-alloc|lifetime|owner|all] 打开pools调试

--enable-malloc-debug 打开BeOS平台上的malloc_debug

--disable-lfs 在32-bit平台上禁用大文件支持(large file support)

--enable-nonportable-atomics 若只打算在486以上的CPU上运行Apache ，那么使用该选项可以启用更加高效的基于互斥执行的原子操作。

--enable-threads 启用线程支持，在线程型的MPM上必须打开它

--disable-threads 禁用线程支持，如果不使用线程化的MPM ，可以关闭它以减少系统开销。

--disable-dso 禁用DSO支持

--enable-other-child 启用可靠子进程支持

--disable-ipv6 禁用IPv6支持可选的额外程序包

--with-gnu-ld 指定C编译器使用 GNU ld

--with-pic 只使用 PIC/non-PIC 对象[默认为两者都使用]

--with-tags[=TAGS] 包含额外的配置

--with-installbuilddir=DIR 指定APR编译文件的存放位置(默认值为：’${datadir}/build’)

--without-libtool 禁止使用libtool连接库文件

--with-efence[=DIR] 指定Electric Fence的安装目录

--with-sendfile 强制使用sendfile(译者注：Linux2.4/2.6内核都支持)

--with-egd[=DIR] 使用EDG兼容的socket

--with-devrandom[=DEV] 指定随机设备[默认为：/dev/random] 用于apr-util的configure脚本的选项：可选的额外程序包

--with-apr=PATH 指定APR的安装目录(–prefix选项值或apr-config的路径)

--with-ldap-include=PATH ldap包含文件目录(带结尾斜线)

--with-ldap-lib=PATH ldap库文件路径

--with-ldap=library 使用的ldap库

--with-dbm=DBM 选择使用的DBM类型DBM={sdbm,gdbm,ndbm,db,db1,db185,db2,db3,db4,db41,db42,db43,db44}

--with-gdbm=PATH 指定GDBM的位置

--with-ndbm=PATH 指定NDBM的位置

--with-berkeley-db=PATH 指定Berkeley DB的位置

--with-pgsql=PATH 指定PostgreSQL的位置

--with-mysql=PATH 参看INSTALL.MySQL文件的内容

--with-sqlite3=PATH 指定sqlite3的位置

--with-sqlite2=PATH 指定sqlite2的位置

--with-expat=PATH 指定Expat的位置或’builtin’

--with-iconv=PATH iconv的安装目录

```

#### apache的编译安装方法

```shell
[root@zhangyz httpd-2.2.15]# tar -xf apache-2.2.15.tar.gz
[root@zhangyz httpd-2.2.15]# cd apache-2.2.15
[root@zhangyz httpd-2.2.15]# ./configure --prefix=/usr/local/apache2 \
--enable-mods-shared=most \
--enable-so \
--enable-rewrite \
--enable-ssl \
--with-mpm=worker
[root@zhangyz httpd-2.2.15]# make
[root@zhangyz httpd-2.2.15]# make install 
```

#### php的编译安装方法
```shell
[root@zhangyz ~]# tar -xf php-5.6.1.tar.gz
[root@zhangyz ~]# cd php-5.6.1
[root@zhangyz php-5.6.31]# ./configure --prefix=/usr/local/php5 \
--with-apxs2=/usr/local/apache2/bin/apxs \
--with-config-file-path=/usr/local/php5/etc \
--with-mysql \
--with-mysqli \
--with-pdo-mysql \
--with-iconv-dir \
--with-freetype-dir \
--with-jpeg-dir \
--with-png-dir \
--with-zlib \
--with-libxml-dir=/usr \
--enable-xml \
--enable-discard-path \
--enable-magic-quotes \
--enable-safe-mode \
--enable-bcmath \
--enable-shmop \
--enable-system \
--enable-inline-optimization \
--with-curl \
--enable-mbregex \
--enable-fastcgi \
--enable-fpm \
--enable-force-cgi-redirect \
--enable-mbstring \
--with-mcrypt \
--enable-ftp \
--with-gd-native-ttf \
--with-openssl \
--with-mhash \
--enable-sockets \
--with-xmlrpc \
--enable-zip \
--enable-soap \
--without-pear \
--with-gettext \
--with-mime-magi
[root@zhangyz php-5.6.31]# make
[root@zhangyz php-5.6.31]# make install 
```

#### 编译安装完成之后的使用方法apache如何关联php在apache的配置文件里面添加如下配置

```shell
[root@zhangyz php-5.6.31]# vim /usr/local/apache2/conf/httpd.conf

Addtype application/x-httpd-php .php .phtml .phps
<IfModule dir_module>
    DirectoryIndex index.shtml index.html index.php
    DirectoryIndex index.html
</IfModule>
```
