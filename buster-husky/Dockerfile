FROM buildpack-deps:buster-scm

WORKDIR /

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y make git zlib1g-dev libssl-dev gperf cmake g++

RUN git clone https://github.com/c0re100/td.git && \
    cd td && \
    git checkout 738a5dd5830ced1ed5cffdc7b45e1a179fedbae0 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2 && \
    cd / && \
    rm -rf /td/
