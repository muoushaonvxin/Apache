	Apache的编译安装方法

	tar -xf apache-2.2.15.tar.gz
	cd apache-2.2.15
	./configure --prefix=/usr/local/apache2 --enable-mods-shared=most --enable-so --enable-rewrite --enable-ssl --with-mpm=worker
	make
	make install 

	php的编译安装方法
	tar -xf php-5.6.1.tar.gz
	cd php-5.6.1
	./configure --prefix=/usr/local/php5 --with-apxs2=/usr/local/apache2/bin/apxs --with-config-file-path=/usr/local/php5/etc --with-mysql --with-mysqli --with-pdo-mysql --with-iconv-dir --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir=/usr --enable-xml --enable-discard-path --enable-magic-quotes --enable-safe-mode --enable-bcmath --enable-shmop --enable-system --enable-inline-optimization --with-curl --enable-mbregex --enable-fastcgi --enable-fpm --enable-force-cgi-redirect --enable-mbstring --with-mcrypt --enable-ftp --with-gd-native-ttf --with-openssl --with-mhash --enable-sockets --with-xmlrpc --enable-zip --enable-soap --without-pear --with-gettext --with-mime-magi
	make
	make install 
