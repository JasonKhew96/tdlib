FROM alpine:latest

WORKDIR /

RUN apk add --update \
        ca-certificates

RUN apk add --update --virtual .build-deps \
        alpine-sdk linux-headers git zlib-dev openssl-dev gperf cmake

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout 782670c7dbf278e0ba07fc7e168f39ac154c7238 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2 && \
    cd / && \
    rm -rf /td/
