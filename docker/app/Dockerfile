FROM php:8.0.8-apache

# 設定ファイルのコピー
COPY php.ini /usr/local/etc/php/
COPY 000-default.conf /etc/apache2/sites-enabled/

# composerのインストール
RUN curl -sS http://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer

# node.jsのインストール
RUN curl -sL https://deb.nodesource.com/setup_lts.x | bash - \
  && apt-get install -y nodejs

# ミドルウェアのインストール
RUN apt-get update \
  && apt-get install -y \
    git \
    zip \
    unzip \
    vim \
    libpng-dev \
    libpq-dev \
  && docker-php-ext-install pdo_mysql

# modRewriteの有効化
RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite