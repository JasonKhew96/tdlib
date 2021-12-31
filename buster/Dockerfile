FROM buildpack-deps:buster-scm

WORKDIR /

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y make git zlib1g-dev libssl-dev gperf cmake g++

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout feffe4153d0d1da2abc1bd419bb1ed6a83896eb7 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2 && \
    cd / && \
    rm -rf /td/
