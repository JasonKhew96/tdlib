FROM alpine:latest

WORKDIR /

RUN apk add --update \
        ca-certificates

RUN apk add --update --virtual .build-deps \
        alpine-sdk linux-headers git zlib-dev openssl-dev gperf cmake

RUN git clone https://github.com/c0re100/td.git && \
    cd td && \
    git checkout 08f8bda33c37b8f45d2ece265cc9d101a87f0941 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2 && \
    cd / && \
    rm -rf /td/
