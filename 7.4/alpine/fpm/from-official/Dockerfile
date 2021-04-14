FROM php:7.4.16-fpm-alpine3.13

# 清华源
# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories;
# 阿里源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories;

RUN apk add --no-cache --virtual .run \
        # memcache
        libmemcached-dev

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
        zlib-dev \
        \
    && docker-php-ext-install pdo_mysql \
    # && docker-php-ext-install igbinary \
    # && docker-php-ext-install msgpack \
    # && docker-php-ext-install memcached \
    && pecl install memcached \
    && docker-php-ext-enable memcached \
    && pecl install redis \
    && pecl install xdebug \
    && docker-php-ext-enable redis xdebug \
    # && pecl install swoole \
    # && docker-php-ext-enable swoole \
    \
    && apk del .build-deps \
    && rm -rf /tmp/pear ~/.pearrc


ENTRYPOINT ["docker-php-entrypoint"]
CMD ["php", "-a"]