##FROM bflash4k/ubuntu:16.04
FROM ubuntu:xenial

MAINTAINER Olivier Guiter

VOLUME galette_app:/var/www/html

RUN apt-get update && apt-get install -y curl bzip2

RUN mkdir -p /var/www/html && cd /var/www/html/ && rm -rf * && \
     curl -O http://download.tuxfamily.org/galette/galette-0.8.3.4.tar.bz2 && \
     tar xjvf galette-0.8.3.4.tar.bz2 && \
     rm galette-0.8.3.4.tar.bz2 && \
     chown -R www-data:www-data /var/www/html && \
     mv galette-0.8.3.4/galette/* /var/www/html

