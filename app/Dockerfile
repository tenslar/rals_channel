FROM alpine:3.10.0

# ハマりポイント１：Laravelが必須とするext以外にもいろいろ足りてない
# Laravelに必要なPHP及びextensionパッケージインストール
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
  php7-session

# composerインストールについてはこちらを参照
# https://getcomposer.org/download/
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php \
  && php -r "unlink('composer-setup.php');" \
  && mv composer.phar /usr/local/bin/composer

ENV appName="test"
WORKDIR /home/$appName

#RUN composer create-project --prefer-dist laravel/laravel $appName \
#  && php composer install \
#  && php artisan key:gen

HEALTHCHECK --interval=5s --timeout=3s --start-period=5s --retries=1 \
  CMD php artisan --version || exit 1

# ハマりポイント２：環境変数はENTRYPOINTやCMDには渡せない
ENTRYPOINT ["php", "artisan", "serve", "--host", "0.0.0.0"]
CMD []
