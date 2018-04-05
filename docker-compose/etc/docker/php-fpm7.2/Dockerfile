FROM phpdockerio/php72-fpm:latest

WORKDIR "/var/app/back"

RUN curl -sL https://getcomposer.org/installer | php -- --install-dir /usr/bin --filename composer

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install \
      php7.2-mysql \
      php7.2-gd \
      php7.2-intl \
      php7.2-dev \
      php-pear \
      make \
      git \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# xdebug
RUN pecl install xdebug\
    && echo "zend_extension=$(find /usr/lib/php/ -name xdebug.so)" > /etc/php/7.2/fpm/conf.d/20-xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /etc/php/7.2/fpm/conf.d/20-xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /etc/php/7.2/fpm/conf.d/20-xdebug.ini \
    && echo "xdebug.idekey=PHP_STORM" >> /etc/php/7.2/fpm/conf.d/20-xdebug.ini \
    && echo "zend_extension=$(find /usr/lib/php/ -name xdebug.so)" > /etc/php/7.2/cli/conf.d/20-xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /etc/php/7.2/cli/conf.d/20-xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /etc/php/7.2/cli/conf.d/20-xdebug.ini \
    && echo "xdebug.idekey=PHP_STORM" >> /etc/php/7.2/cli/conf.d/20-xdebug.ini
