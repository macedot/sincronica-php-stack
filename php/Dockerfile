FROM php:7.3.11-fpm
#FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libmcrypt-dev \
	libpng-dev \
	libjpeg-dev \
	libxml2-dev \
	openssl \
	libcurl4-openssl-dev \
	libzip-dev \
	bzip2 \
	&& docker-php-ext-install -j$(nproc) iconv \
	&& docker-php-ext-configure gd \
	--enable-mbstring \
	--enable-zip \
	--enable-sockets \
	--enable-mysqlnd \
	--with-openssl \
	--with-gd \
	--with-xmlrpc \
	--with-mcrypt \
	--with-iconv \
	--with-bz2 \
	--with-curl \
	--with-mysqli=mysqlnd \
	--with-pdo-mysql=mysqlnd \
	--with-png-dir=/usr/include/ \
	--with-jpeg-dir=/usr/include/ \
	--with-freetype-dir=/usr/include/ \
	--with-zlib \
	--with-gettext \
	&& docker-php-ext-install gd mysqli pdo_mysql zip opcache

RUN pecl install xdebug \
	&& pecl install redis \
	&& pecl install mcrypt-1.0.3 \
	&& docker-php-ext-enable xdebug redis mcrypt