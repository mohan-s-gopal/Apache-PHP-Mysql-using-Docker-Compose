FROM php:7.2-apache

COPY ./apache/wordpress.conf /etc/apache2/sites-available/ 

RUN a2ensite wordpress.conf

RUN apt-get update && apt-get install -y --no-install-recommends git zip \
  libfreetype6-dev \
  vim \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev libxslt-dev  \
  && docker-php-ext-install iconv \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install gd

RUN docker-php-ext-install bcmath
RUN docker-php-ext-install xsl 
RUN docker-php-ext-install intl
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install soap
RUN docker-php-ext-install zip
RUN docker-php-ext-install mysqli

RUN curl --silent --show-error https://getcomposer.org/installer | php
