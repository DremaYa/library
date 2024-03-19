# PHP Docker image for Yii 2.0 Framework runtime
# ==============================================

FROM yiisoftware/yii2-php:7.4-fpm-nginx

ARG USER_ID
ARG GROUP_ID

WORKDIR /var/www
ADD composer.* /var/www/

RUN /usr/local/bin/composer install --prefer-dist
ADD ./ /var/www
ENV PATH /var/www/backend/vendor/bin:${PATH}

RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp
RUN docker-php-ext-install -j$(nproc) iconv mysqli pdo_mysql zip gd soap json xsl xml intl curl

RUN pecl install xdebug-2.9.0 imagick redis mcrypt
RUN docker-php-ext-enable imagick xdebug redis mcrypt

RUN usermod -u $USER_ID www-data && groupmod -g $GROUP_ID www-data
USER "${USER_ID}:${GROUP_ID}"



