FROM php:7.4.16-fpm-alpine3.13

RUN apk add --no-cache --virtual .run \
        # memcache
        libmemcached

# php 编译环境
ENV PHPIZE_DEPS \
		autoconf \
		dpkg-dev dpkg \
		file \
		g++ \
		gcc \
		libc-dev \
		make \
		pkgconf \
		re2c

RUN apk add --no-cache --virtual .build-deps \
	    $PHPIZE_DEPS \
        zlib-dev
        \
    && docker-php-ext-install pdo_mysql \
    # && docker-php-ext-install igbinary \
    # && docker-php-ext-install msgpack \
    && pecl install memcached \
    && pecl install redis \
    && pecl install swoole \
    && pecl install xdebug \
    && docker-php-ext-enable memcached redis swoole xdebug \
    \
    && apk del .build-deps \
    && rm -rf /tmp/pear ~/.pearrc


ENTRYPOINT ["docker-php-entrypoint"]
CMD ["php", "-a"]