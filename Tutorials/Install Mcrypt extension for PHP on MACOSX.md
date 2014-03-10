== Install libmcrypt extension for php on MACOSX 10.9

1. Download the source

- Download the code for libmcrypt (here)[http://sourceforge.net/projects/mcrypt/files/Libmcrypt/2.5.8/]

- Download the php(5.4.17) code (here)[http://museum.php.net/php5/php-5.4.17.tar.bz2]

- Extract all to ~/php/mcrypt

- Go to libmcrypt folder and follow these steps:

	$ MACOSX_DEPLOYMENT_TARGET=10.9 CFLAGS='-O3 -fno-common -arch i386 -arch x86_64' LDFLAGS='-O3 -arch i386 -arch x86_64' CXXFLAGS='-O3 -fno-common -arch i386 -arch x86_64' ./configure --disable-dependency-tracking
	$ make -j6
	$ sudo make install

- Now for the PHP extension
	$ cd ~/php/mcrypt/php-5.4.17/ext/mcrypt
	$ brew install autoconf
	$ /usr/bin/phpize
	$ MACOSX_DEPLOYMENT_TARGET=10.9 CFLAGS='-O3 -fno-common -arch i386 -arch x86_64' LDFLAGS='-O3 -arch i386 -arch x86_64' CXXFLAGS='-O3 -fno-common -arch i386 -arch x86_64' ./configure --with-php-config=/usr/bin/php-config
	$ make -j6
	$ make test
	$ sudo make install

- Check PHP
	$ sudo chmod 777 /etc/php.ini.default
	$ cp /etc/php.ini.default /etc/php.ini
	Check enable_dl = On
	Add extension=mcrypt.so to Extension Section

- You're done