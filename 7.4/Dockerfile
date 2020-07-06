FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql \
    && DEBIAN_FRONTEND=noninteractive apt-get install tzdata vim -y \
    && ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
    

# composer 설치
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" && \
    mv composer.phar /usr/bin/composer
    
# php.ini 에 timezone 설정 추가
RUN printf '[PHP]\ndate.timezone = "Asia/Seoul"\n' > /usr/local/etc/php/conf.d/tzone.ini

# 정리
RUN apt-get autoremove -y && apt-get clean -y && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
