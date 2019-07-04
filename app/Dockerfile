FROM alpine:3.10

LABEL maintainer="tensler906 / (Twitter: @tensler906)" \
  description="Image to run simply Laravel application."

RUN apk --update --no-cache add \ 
  php7 \
  php7-json \ 
  php7-bcmath \ 
  php7-ctype \
  php7-mbstring \
  php7-openssl \
  php7-pdo \
  php7-pdo_mysql \
  php7-tokenizer \
  php7-xml \
  php7-phar \
  php7-dom \
  php7-xmlwriter \
  php7-session \
  php7-opcache \
  php7-pecl-xdebug

RUN { \
  echo 'display_errors=1'; \
  echo 'error_reporting=E_ALL'; \
  echo 'opcache.enable=1'; \
  echo 'opcache.enable_cli=1'; \
  echo 'opcache.validate_timestamps=1'; \
  echo 'opcache.memory_consumption=64'; \
  echo 'opcache.interned_strings_buffer=4'; \
  echo 'opcache.max_accelerated_files=4000'; \
  echo 'opcache.revalidate_freq=60'; \
  echo 'opcache.fast_shutdown=1'; \
  echo 'xdebug.remote_enable=1'; \
  echo 'xdebug.remote_autostart=1'; \
  echo 'xdebug.remote_host=host.docker.internal'; \
  echo 'xdebug.remote_port=9010'; \
  echo 'zend_extension=xdebug.so'; \
  echo 'xdebug.remote_log=/tmp/xdebug.log'; \
} > /etc/php7/conf.d/overrides.ini

WORKDIR /var/www/html

#RUN composer create-project --prefer-dist laravel/laravel $appName \
#  && php composer install \
#  && php artisan key:gen

HEALTHCHECK --interval=5s --timeout=3s --start-period=5s --retries=1 \
  CMD php artisan --version || exit 1
