ARG PHP_ALPINE_VERSION=8.1
FROM --platform=${BUILDPLATFORM} php:${PHP_ALPINE_VERSION}

# Install packages required to compile php extensions
RUN apk add \
    autoconf \
    zlib-dev \
    g++ \
    grpc-dev \
    cmake \
    linux-headers \
    make

RUN yes | pecl install grpc \
    && docker-php-ext-enable grpc

RUN \
    set -eux \
    \
    && find "$(php-config --extension-dir)" -name '*.so' -type f -exec strip --strip-all {} \;