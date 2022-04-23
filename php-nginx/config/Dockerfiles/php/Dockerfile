FROM php:7.4.28-fpm-alpine3.15
LABEL autor="Carlos Carpintero" version="1.0"
COPY xdebug.ini /usr/local/etc/php/conf.d
COPY after.sh /home
RUN apk add nano zip git
RUN chmod +x /home/after.sh && \
    sh /home/after.sh
RUN apk --update --no-cache add autoconf g++ make && \
    pecl install -f xdebug-2.9.2 && \
    pecl config-set php_ini /usr/local/etc/php/php.ini-development && \
    cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini && \
    rm /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini-production && \
    apk del --purge autoconf g++ make
RUN docker-php-ext-enable xdebug
# RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20190902/xdebug.so" >> /usr/local/etc/php/php.ini-development
WORKDIR /public_html
