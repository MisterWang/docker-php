FROM alpine:3.13

# 需要软件
# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories;
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories;

RUN apk add --no-cache --virtual .composer-rundeps \
    bash \
    coreutils \
    git \
    make \
    mercurial \
    openssh-client \
    patch \
    subversion \
    tini \
    unzip \
    zip

RUN apk add --no-cache --virtual .php \ 
        bash \
        php7 \
        php7-cli \
        # php7-pdo \
        # php7-pdo_mysql \
        php7-gd \
        php7-bcmath \
        php7-zlib \
        php7-mbstring \
        # php7-mysqlnd \
        php7-xml \
        php7-json \
        # php7-iconv \
        php7-sockets \
        # php7-session \
        php7-sodium \
        php7-curl \
        php7-dom \
        php7-fileinfo \
        php7-openssl \
        php7-zlib \
        php7-zip \
        php7-xml \
        php7-opcache \
        php7-simplexml \
        php7-xmlreader \
        # php7-pecl-redis \
        # php7-pecl-imagick \
        \
        composer \
    \
    && apk del --purge *-dev \
    # && rm /etc/php7/php-fpm.d/www.conf \
    && rm -rf /var/cache/apk/* /tmp/* /usr/share/man /usr/share/php7

RUN apk add --no-cache --virtual .ext \
        php7-ctype \
        php7-tokenizer \
        php7-xmlwriter \
    \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer

COPY docker-php-entrypoint /

ENTRYPOINT ["/bin/sh","/docker-php-entrypoint"]
WORKDIR /var/www/html

# EXPOSE 9000
CMD ["composer"]