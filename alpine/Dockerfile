FROM alpine:3.13

WORKDIR /

RUN apk add --update \
        ca-certificates

RUN apk add --update --virtual .build-deps \
        g++ \
        make \
        cmake \
        git \
        gperf \
        libressl-dev \
        zlib-dev \
        zlib-static \
        linux-headers \
        alpine-sdk \
        openssl-dev \
        php

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout 5bd0c2c46ded5c75a641829cfe84c0b5fead5bfc && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target prepare_cross_compiling && \
    cd .. && \
    php SplitSource.php && \
    cd build && \
    cmake --build . --target install
