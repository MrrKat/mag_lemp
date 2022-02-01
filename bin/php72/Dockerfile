FROM php:7.2-fpm
RUN apt-get -y update --fix-missing && \
    apt-get upgrade -y
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN apt-get -y update && \
    apt-get -y --no-install-recommends install nano wget \
dialog && \
    apt-get -y --no-install-recommends install default-mysql-client \
zlib1g-dev \
libzip-dev \
libicu-dev && \
    apt-get -y --no-install-recommends install --fix-missing apt-utils \
build-essential \
git \
curl \
libonig-dev && \
    apt-get -y --no-install-recommends install --fix-missing libcurl4 \
libcurl4-openssl-dev \
zip \
openssl
RUN pecl install redis-5.3.3 && \
    docker-php-ext-enable redis
RUN apt-get --no-install-recommends install -y libfreetype6-dev \
libjpeg62-turbo-dev \
libpng-dev && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-install gd
RUN docker-php-ext-install bcmath intl
# PHP-soap
RUN apt update && apt-get -y --no-install-recommends install --fix-missing libxml2-dev && docker-php-ext-install soap
RUN pecl install xdebug && docker-php-ext-enable xdebug
RUN apt update && apt-get -y --no-install-recommends install --fix-missing libxslt1-dev python-dev && docker-php-ext-install xsl zip opcache
RUN docker-php-ext-install sockets
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN mkdir -p /etc/nginx/ssl

EXPOSE 80
EXPOSE 443
