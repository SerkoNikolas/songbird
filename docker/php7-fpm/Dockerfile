FROM debian:stretch-slim

RUN export LC_ALL=C.UTF-8

RUN apt-get -y update && apt-get -y upgrade

RUN apt-get install -y --no-install-recommends \
    git-core \
    nano \
    libssl-dev \
    curl \
    bash \
    wget \
    openssl \
    imagemagick \
    apt-transport-https \
    ca-certificates \
    gcc \
    libpcre3-dev \
    make

RUN apt-get install -y --no-install-recommends \
    php7.0 \
    php7.0-dev \
    php7.0-common \
    php7.0-fpm \
    php7.0-pdo \
    php7.0-mysqli \
    php7.0-pgsql \
    php7.0-bcmath \
    php7.0-cli \
    php7.0-curl \
    php7.0-mcrypt \
    php7.0-mbstring \
    php7.0-ctype \
    php7.0-gd \
    php7.0-exif \
    php7.0-intl \
    php7.0-sqlite3 \
    php7.0-xml \
    php7.0-xsl \
    php7.0-curl \
    php7.0-bz2 \
    php7.0-iconv \
    php7.0-json \
    php7.0-phar \
    php7.0-posix \
    php7.0-soap \
    php7.0-dom \
    php7.0-zip \
    php7.0-redis \
#    php7.0-xdebug \
    php7.0-memcached \
    php7.0-tokenizer \
    php7.0-simplexml \
    php7.0-opcache \
    php7.0-apcu

RUN git config --global user.email "nikolas.serko@gmail.com" \
    && git config --global user.name "Nikolas Serko" \
    && git config --global push.default current

#RUN adduser -G www-data -s /usr/sbin/nologin -H -D www-data
RUN ln -s /usr/sbin/php-fpm7.0 /usr/bin/php-fpm

RUN mkdir -p /code && \
    chmod 775 /code

WORKDIR /code

RUN mkdir -p /usr/local/bin && \
    curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony && \
    chmod a+x /usr/local/bin/symfony

# Install composer global bin
RUN wget -qO- https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    chmod a+x /usr/local/bin/composer

RUN adduser -s /bin/bash -D -h /home/serko -u 1111 serko

RUN rm -rf /var/lib/apt/lists/*

#USER serko

EXPOSE 9000

#CMD ["/bin/bash"]
#CMD ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]
#CMD ["/bin/bash"]
#CMD ["/start.sh"]
#CMD ["nginx", "-g", "daemon off;"]
#ENTRYPOINT ["php-fpm7", "-F"]
ENTRYPOINT ["/usr/bin/php-fpm", "-F"]