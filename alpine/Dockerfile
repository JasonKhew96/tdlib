FROM alpine:latest

WORKDIR /

RUN apk add --update \
        ca-certificates

RUN apk add --update --virtual .build-deps \
        alpine-sdk linux-headers git zlib-dev openssl-dev gperf cmake

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout 92c2a9c4e521df720abeaa9872e1c2b797d5c93f && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2 && \
    cd / && \
    rm -rf /td/
