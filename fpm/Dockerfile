ARG PHP_FPM_VERSION=8.1
FROM --platform=${BUILDPLATFORM} php:${PHP_FPM_VERSION}

# Install packages required to compile php extensions
RUN apt-get update && apt-get install -y \
    autoconf \
    zlib1g-dev \
    g++

RUN yes | pecl install grpc \
    && docker-php-ext-enable grpc

RUN \
    set -eux \
    \
    && find "$(php-config --extension-dir)" -name '*.so' -type f -exec strip --strip-all {} \;