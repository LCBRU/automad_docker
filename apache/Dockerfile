FROM php:7-apache
LABEL maintainer="Richard Bramley <rabramley@gmail.com>"

COPY php.ini $PHP_INI_DIR/

ARG THEME

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y zip libjpeg-dev libpng-dev

RUN a2enmod rewrite
RUN docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr
RUN docker-php-ext-install gd
RUN docker-php-ext-install exif

WORKDIR /var/www/
RUN rm -fR /var/www/html

ADD https://automad.org/download automad.zip
RUN unzip automad.zip
RUN rm automad.zip
RUN mv marc* html

RUN rm -fR html/packages/*
ADD https://github.com/LCBRU/${THEME}/archive/master.zip ${THEME}.zip
RUN unzip ${THEME}.zip
RUN rm ${THEME}.zip
RUN mv ${THEME}-master html/packages/${THEME}

RUN chown -R www-data:www-data /var/www/html/cache