FROM php:7.0-apache
MAINTAINER Richard Bramley <rabramley@gmail.com>

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y zip vim libjpeg-dev libpng-dev

RUN a2enmod rewrite
RUN docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr
RUN docker-php-ext-install gd
RUN docker-php-ext-install exif

WORKDIR /var/www/

ADD automad.0.10.zip /var/www
RUN unzip /var/www/automad.0.10.zip
RUN rm -fR /var/www/html
RUN mv /var/www/*automad*/www html
ADD accounts.php /var/www/html/config/
RUN chown -R www-data:www-data /var/www/html/

