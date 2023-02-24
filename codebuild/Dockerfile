# docker/nginx/Dockerfile
FROM 605903052402.dkr.ecr.ap-northeast-1.amazonaws.com/nginx-php-fpm

ADD ./cloudbuild/conf/nginx/nginx.conf /etc/nginx/conf.d/default.conf

ENV DEBIAN_FRONTEND noninteractive
ENV SOURCE_ROOT /var/www/app

# SOAP
RUN apt-get -y update
RUN apt-get -y install libxml2-dev php8.0-soap

COPY . $SOURCE_ROOT
WORKDIR $SOURCE_ROOT

RUN chmod -R a+w storage/ bootstrap/cache
RUN php artisan config:clear
RUN php artisan cache:clear
RUN php artisan optimize:clear
