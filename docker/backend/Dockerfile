FROM php:8.3-apache

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN #curl -sSk https://getcomposer.org/installer | php -- --disable-tls && mv composer.phar /usr/local/bin/composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

RUN apt-get update && apt-get -y install libzip-dev libicu-dev

RUN docker-php-ext-install pdo_mysql intl zip

RUN pecl install xdebug-3.3.1 \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.mode=coverage" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony5/bin/symfony /usr/local/bin/

RUN apt-get install git -y \
    && git config --global user.email "you@example.com" \
    && git config --global user.name "Your Name"

#RUN cd /usr/local/etc/php/conf.d/ && \
#  echo 'memory_limit = -1' >> /usr/local/etc/php/conf.d/docker-php-ram-limit.ini

#COPY . /var/www/
#COPY ./docker/vhost/apache.conf /etc/apache2/sites-available/000-default.conf

WORKDIR /var/www/
#ENV COMPOSER_ALLOW_SUPERUSER = 1
#RUN composer install

ENTRYPOINT ["bash", "./docker.sh"]

EXPOSE 80 25
