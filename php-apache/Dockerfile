FROM php:7.4.28-apache
LABEL autor="Carlos Carpintero" version="1.0"
RUN apt-get update && \
    apt-get install -y nano zip git && \
    pecl install xdebug && \
    rm -Rf /var/lib/apt/lists/*
RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20190902/xdebug.so" >> /usr/local/etc/php/php.ini-development && \
    cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini && \
    rm /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini-production && \
    echo "xdebug.mode=debug,trace,develop\nxdebug.start_with_request=yes\nxdebug.discover_client_host=0\nxdebug.client_host=172.20.0.2\nxdebug.client_port=9003\nxdebug.idekey=docker" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN docker-php-ext-enable xdebug && \
    pecl config-set php_ini /usr/local/etc/php/php.ini
COPY ./config/after.sh /home
RUN chmod +x /home/after.sh && \
    sh /home/after.sh
COPY ./config/000-default.conf /etc/apache2/sites-available/
WORKDIR /var/www/html
