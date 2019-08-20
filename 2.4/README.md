
```shell
[root@zhangyz ~]# yum install -y apr-devel apr-util-devel openssl-devel libevent-devel pcre-devel
```

下载所需软件包，要安装新版本：

```shell
[root@zhangyz ~]# cd /usr/local/src
[root@zhangyz src]# wget http://archive.apache.org/dist/apr/apr-1.4.5.tar.gz
[root@zhangyz src]# wget http://archive.apache.org/dist/apr/apr-util-1.3.12.tar.gz
[root@zhangyz src]# wget http://jaist.dl.sourceforge.net/project/pcre/pcre/8.10/pcre-8.10.zip
```

先将相关的关联包进行源码安装

1.安装 apr-1.4.5.tar.gz

```shell
[root@zhangyz src]# tar -xf apr-1.4.5.tar.gz
[root@zhangyz src]# cd apr-1.4.5
[root@zhangyz apr-1.4.5]# ./configure --prefix=/usr/local/apr
[root@zhangyz apr-1.4.5]# make && make install
```

2.安装 apr-util-1.3.12.tar.gz

```shell
[root@zhangyz src]# tar -xf apr-util-1.3.12.tar.gz
[root@zhangyz src]# cd apr-util-1.3.12
[root@zhangyz apr-util-1.3.12]# ./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr/bin/apr-1-config 
[root@zhangyz apr-util-1.3.12]# make && make install
```

3.安装 pcre-8.10.zip 

```shell
[root@zhangyz src]# unzip pcre-8.10.zip 
[root@zhangyz cd]# cd pcre-8.10
[root@zhangyz pcre-8.10]# ./configure --disable-shared --with-pic --prefix=/usr/local/pcre 
[root@zhangyz pcre-8.10]# make && make install
```

4.安装 httpd-2.4.41.tar.gz

```shell
[root@zhangyz src]# tar -xf httpd-2.4.41.tar.gz
[root@zhangyz src]# cd httpd-2.4.41
[root@zhangyz httpd-2.4.41]# ./configure --prefix=/usr/local/apache2.4.41 --with-apr-util=/usr/local/apr-util/ --with-apr=/usr/local/apr --with-pcre=/usr/local/pcre/ --enable-mods-shared=most --enable-so --enable-rewrite --enable-ssl --with-mpm=worker
[root@zhangyz httpd-2.4.41]# make
[root@zhangyz httpd-2.4.41]# make install
```
