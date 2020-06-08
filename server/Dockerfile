FROM php:apache

RUN apt-get update && \
# 1. development packages
    apt-get install -y \
    git \
    zip \
    curl \
    sudo \
    unzip \
    libicu-dev \
    libzip-dev \
    libbz2-dev \
    libpng-dev \
    libjpeg-dev \
    libmcrypt-dev \
    libreadline-dev \
    libfreetype6-dev \
    g++

# 2. start with base php config, then add extensions
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini" && \
    docker-php-ext-install \
    bz2 \
    intl \
    iconv \
    bcmath \
    opcache \
    calendar \
    pdo_mysql \
    zip  \
	mysqli
	
# 3. other packages
RUN curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash - && \
	apt-get install -y nodejs \
	python \
	python3-pip \
	nano

# 4 composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# 5. we need a user with the same UID/GID with host user
# so when we execute CLI commands, all the host file's ownership remains intact
# otherwise command from inside container will create root-owned files and directories
ARG uid
RUN useradd -G www-data,root -u $uid -d /home/devuser devuser && \
    mkdir -p /home/devuser/.composer && \
    chown -R devuser:devuser /home/devuser

EXPOSE 8000 5000 3000
