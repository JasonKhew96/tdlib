FROM alpine:latest

WORKDIR /

RUN apk add --update \
        ca-certificates

RUN apk add --update --virtual .build-deps \
        alpine-sdk linux-headers git zlib-dev openssl-dev gperf php cmake

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout 7d41d9eaa58a6e0927806283252dc9e74eda5512 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2
