FROM php:7.4-fpm

#RUN pecl install redis-5.1.1 \
#    pecl install xdebug-2.8.1 \
#    && docker-php-ext-enable redis xdebug

#######composer
COPY --from=composer/composer:latest-bin /composer /usr/bin/composer
RUN composer config -g repo.packagist composer "https://mirrors.aliyun.com/composer/"

#######设置国内软件源
RUN cp /etc/apt/sources.list /etc/apt/sources.list.bak \
    &&cat /dev/null > /etc/apt/sources.list

COPY sources.list /etc/apt/sources.list

#RUN echo 'deb https://mirrors.zju.edu.cn/debian/ bullseye main contrib non-free \
#    deb https://mirrors.zju.edu.cn/debian/ bullseye-updates main contrib non-free \
#    deb https://mirrors.zju.edu.cn/debian/ bullseye-backports main contrib non-free \
#    deb https://mirrors.zju.edu.cn/debian-security bullseye-security main contrib non-free' >> /etc/apt/sources.list

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
RUN install-php-extensions gd zip bz2 opcache \
#    xlswriter  \
#    zstd lzf igbinary redis \
#    amqp
    pdo_mysql mysqli

#########依赖安装
RUN apt-get update && apt-get install unzip p7zip-full git -y && apt-get clean
