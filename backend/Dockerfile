FROM php:8.2.1-fpm as php

ENV APP_ENV=php
ENV APP_DEBUG=true
ENV COMPOSER_ALLOW_SUPERUSER=1

# ARG AWS_ACCESS_KEY_ID
# ARG AWS_SECRET_ACCESS_KEY
# ARG AWS_DEFAULT_REGION

RUN apt-get update
RUN apt-get -y install zsh htop zip unzip git awscli vim
RUN curl -sSL https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions -o - | sh -s \
      gd \
      mysqli \
      bcmath \
      zip \
      soap \
      sockets \
      exif

COPY --from=composer:2.3  /usr/bin/composer /usr/bin/composer
# RUN git clone http://weijie:jieHuang1108@35.73.12.167/wms/wms-backend.git /var/www/html/wms-backend
# RUN git clone http://weijie:jieHuang1108@35.73.12.167/wms/wms-frontend.git /var/www/html/wms-frontend
# RUN composer --version && php -v

# WORKDIR "/var/www/html/wms-backend"
# RUN git checkout --track origin/feature/upgrade-laravel-9 && git pull origin feature/upgrade-laravel-9

# RUN export AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}
# RUN export AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}
# RUN export AWS_DEFAULT_REGION=${AWS_DEFAULT_REGION}

# RUN aws ssm get-parameter --with-decryption --name /backend/test/.common.env:5 --output text --query 'Parameter.Value' > .common.env
# RUN aws ssm get-parameter --with-decryption --name /backend/test/.logistics.env --output text --query 'Parameter.Value' > .logistics.env
# RUN cat .common.env .logistics.env > .env
# RUN rm .common.env .logistics.env

# RUN chmod 777 -R storage/