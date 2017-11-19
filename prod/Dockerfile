FROM php:7.1-fpm
LABEL maintainer="ivan.binzz.borysenko@gmail.com"

RUN echo "deb http://us.archive.ubuntu.com/ubuntu/ precise main universe" >> /etc/apt/source.list

# Install Composer

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set timezone
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Kiev /etc/localtime
RUN "date"


# Extensions
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-configure bcmath
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install sockets
RUN docker-php-ext-install zip


# git libssl
RUN apt-get update \
    && apt-get install git libssl-dev -y

# AMQP
RUN curl -L -o /tmp/rabbitmq.tar.gz https://github.com/alanxz/rabbitmq-c/releases/download/v0.8.0/rabbitmq-c-0.8.0.tar.gz \
    && tar xfz /tmp/rabbitmq.tar.gz \
    && rm -r /tmp/rabbitmq.tar.gz \
    && cd rabbitmq-c-0.8.0 \
    && ./configure \
    && make \
    && make install \
    && echo "OK"

RUN pecl install amqp
RUN docker-php-ext-enable amqp

WORKDIR /var/www/symfony

RUN usermod -u 1000 www-data

RUN echo 'alias sf="php bin/console"' >> ~/.bashrc
CMD ["php-fpm"]