
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
