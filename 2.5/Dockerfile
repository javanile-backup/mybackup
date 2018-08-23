## LAMP with PHP 7.2
FROM php:5.6-apache
LABEL MAINTAINER="Francesco Bianco <info@javanile.org>"
WORKDIR /var/www/html

## Settings
ENV MB_SRC=http://sourceforge.net/projects/phpmybackup/files/phpMyBackupPro
ENV MB_VER=2.5

## Install dependencies
RUN apt-get update \
 && apt-get install -y --no-install-recommends unzip \
 && docker-php-ext-install mysql \
 && rm -rf /var/lib/apt/lists/*

## Download
RUN curl -o mb.zip -SL ${MB_SRC}/phpMyBackupPro%20${MB_VER}/phpMyBackupPro-${MB_VER}.zip \
 && unzip -q mb && rm mb.zip && mv phpMyBackupPro-${MB_VER} mybackup

## Running
COPY foreground.sh /usr/local/bin/
CMD ["foreground.sh"]
