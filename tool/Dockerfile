FROM php:7.4-cli

#RUN pecl install xdebug-2.8.1 \
#	&& docker-php-ext-enable xdebug



#RUN pecl install swoole-4.8.5 \
#	pecl install redis-5.1.1 \
#	&& docker-php-ext-enable swoole redis

COPY --from=composer/composer:latest-bin /composer /usr/bin/composer
RUN composer config -g repo.packagist composer "https://mirrors.aliyun.com/composer/"




#COPY composer.phar /usr/bin
#RUN cp /usr/bin/composer.phar /usr/bin/composer \
#    && chmod +X /usr/bin/composer
##	&& composer
