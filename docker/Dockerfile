FROM redhat/ubi9-minimal:9.3-1552

ARG PARALLELISM=4
ARG CMAKE_VERSION=3.28.3

RUN microdnf install tar gzip gcc gcc-c++ glibc-devel zlib-devel libstdc++-static openssl-devel -y

RUN cd /tmp && \
    curl -L -O https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}.tar.gz && \
    tar -xzf cmake-${CMAKE_VERSION}.tar.gz && \
    cd cmake-${CMAKE_VERSION} && \
    ./bootstrap --parallel=${PARALLELISM} && \
    make -j ${PARALLELISM} install && \
    cd - && \
    rm -rf /tmp/cmake-${CMAKE_VERSION}

ENTRYPOINT [ "sleep" ]

CMD [ "60" ]