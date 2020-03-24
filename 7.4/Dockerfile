FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql

# composer 설치
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" && \
    mv composer.phar /usr/bin/composer

# 정리
RUN apt-get autoremove -y && apt-get clean -y && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*