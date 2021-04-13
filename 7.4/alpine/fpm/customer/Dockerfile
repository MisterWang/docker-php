FROM alpine:3.13

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories;

RUN apk add --no-cache --virtual .php \ 
        php7 \
        php7-fpm \
        php7-pdo \
        php7-pdo_mysql \
        php7-gd \
        php7-bcmath \
        php7-zlib \
        php7-mbstring \
        php7-mysqlnd \
        php7-xml \
        php7-json \
        php7-iconv \
        php7-sockets \
        php7-session \
        php7-sodium \
        php7-curl \
        php7-dom \
        php7-fileinfo \
        php7-openssl \
        php7-zlib \
        php7-xml \
        php7-opcache \
        php7-pecl-redis \
        php7-pecl-imagick \
    \
    # 注释listen配置(默认是127.0.0.1)
    && sed -i '/listen =/{s/l/; l/}' /etc/php7/php-fpm.d/www.conf \
    \
    && apk del --purge *-dev \
    # && rm /etc/php7/php-fpm.d/www.conf \
    && rm -rf /var/cache/apk/* /tmp/* /usr/share/man /usr/share/php7

# 配置fpm
COPY docker-fpm.conf /etc/php7/php-fpm.d/docker-fpm.conf

COPY docker-php-entrypoint /usr/local/bin/

# ENTRYPOINT ["docker-php-entrypoint"]
WORKDIR /var/www/html

EXPOSE 9000
CMD ["php-fpm7"]