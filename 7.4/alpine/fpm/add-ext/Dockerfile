FROM php74:fpm

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories;

RUN apk add --no-cache \ 
        php7-simplexml \
        php7-xmlwriter \
    \
    && apk del --purge *-dev \
    && rm -rf /var/cache/apk/* /tmp/* 
    # /usr/share/man /usr/share/php7

WORKDIR /var/www/html