FROM buildpack-deps:buster-scm

WORKDIR /

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y make git zlib1g-dev libssl-dev gperf php-cli cmake clang libc++-dev libc++abi-dev

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout 7d41d9eaa58a6e0927806283252dc9e74eda5512 && \
    mkdir build && \
    cd build && \
    CXXFLAGS="-stdlib=libc++" CC=/usr/bin/clang CXX=/usr/bin/clang++ cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j 2
