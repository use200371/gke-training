FROM php:fpm-alpine

RUN exec >& /root/build.log ;\
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer; \
    /usr/local/bin/composer config -g repos.packagist composer https://packagist.jp; \
    /usr/local/bin/composer global require "hirak/prestissimo"; \
    /usr/local/bin/composer global require "laravel/installer"; \
    apk update; \
    apk add zlib-dev; \
    docker-php-ext-install zip;
ENV PATH /root/.composer/vendor/bin:$PATH
ADD zz-docker.conf /usr/local/etc/php-fpm.d/
ADD www.conf /usr/local/etc/php-fpm.d/