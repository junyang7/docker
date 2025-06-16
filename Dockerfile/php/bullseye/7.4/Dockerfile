FROM php:7.4-fpm-bullseye
COPY ./src /tmp/src
WORKDIR /
RUN apt-get update \
    && apt-get install -y --no-install-recommends  \
    ca-certificates  \
    apt-transport-https  \
    wget  \
    gnupg  \
    procps  \
    telnet  \
    iputils-ping  \
    strace  \
    netcat  \
    iproute2  \
    libc6  \
    libc6-dev  \
    net-tools  \
    less  \
    tar  \
    gzip  \
    bzip2  \
    xz-utils  \
    dnsutils  \
    lsof  \
    uuid-dev  \
    libssl-dev  \
    util-linux  \
    autoconf  \
    gcc  \
    g++  \
    make  \
    libpng-dev  \
    libbz2-dev  \
    libgettextpo-dev  \
    gettext  \
    libxslt-dev  \
    libgmp-dev  \
    libldap2-dev  \
    librdkafka-dev  \
    libevent-dev  \
    libyaml-dev  \
    libssh2-1-dev  \
    libzip-dev  \
    bash  \
    curl  \
    vim  \
    zsh  \
    git \
    cron \
    && docker-php-ext-install -j$(nproc) gd opcache bz2 bcmath exif calendar sockets mysqli pcntl pdo_mysql shmop sysvmsg sysvsem sysvshm zip gettext xsl gmp ldap ctype dba phar soap xmlrpc \
    && pecl install /tmp/src/pecl/igbinary-3.2.7.tgz && docker-php-ext-enable igbinary \
    && pecl install /tmp/src/pecl/protobuf-3.21.4.tgz && docker-php-ext-enable protobuf \
    && pecl install /tmp/src/pecl/redis-5.3.7.tgz && docker-php-ext-enable redis \
    && pecl install /tmp/src/pecl/xdebug-3.1.5.tgz && docker-php-ext-enable xdebug \
    && pecl install /tmp/src/pecl/event-3.0.8.tgz && docker-php-ext-enable --ini-name docker-php-ext-zevent.ini event \
    && pecl install /tmp/src/pecl/yaml-2.2.2.tgz && docker-php-ext-enable yaml \
    && pecl install /tmp/src/pecl/zstd-0.11.0.tgz && docker-php-ext-enable zstd \
    && pecl install /tmp/src/pecl/xmldiff-1.1.3.tgz && docker-php-ext-enable xmldiff \
    && pecl install /tmp/src/pecl/uuid-1.2.0.tgz && docker-php-ext-enable uuid \
    && pecl install /tmp/src/pecl/ssh2-1.3.1.tgz && docker-php-ext-enable ssh2 \
    && pecl install /tmp/src/pecl/swoole-4.8.11.tgz && docker-php-ext-enable swoole \
    && pecl install /tmp/src/pecl/inotify-3.0.0.tgz && docker-php-ext-enable inotify \
    && pecl install /tmp/src/pecl/rdkafka-6.0.5.tgz && docker-php-ext-enable rdkafka \
    && pecl install /tmp/src/pecl/grpc-1.48.0.tgz && docker-php-ext-enable grpc \
    && php /tmp/src/composer/composer-setup.php && mv composer.phar /usr/local/bin/composer \
    && sh /tmp/src/ohmyzsh/install.sh \
    && sed -i -e "s/bin\/bash/bin\/zsh/" /etc/passwd \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/pear \
    && rm -rf /tmp/src
