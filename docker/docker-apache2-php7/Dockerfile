FROM ubuntu:xenial

MAINTAINER Olivier Guiter

# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y curl \
    apache2 \
    php7.0 php7.0-cli php-redis php-tidy php-gettext php-xdebug php-mbstring php-gd \
    php7.0-zip php7.0-mcrypt php7.0-curl php7.0-dom php7.0-mbstring php7.0-mysql php-imagick libapache2-mod-php7.0 composer wget curl git

RUN phpenmod mcrypt && rm -rf /var/lib/apt/lists/* 

RUN a2enmod rewrite headers php7.0

COPY ./apache/ /etc/apache2/sites-available/

WORKDIR /var/www
RUN rm -rf *

EXPOSE 80
CMD /usr/sbin/apache2ctl -D FOREGROUND
