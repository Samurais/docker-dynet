FROM ubuntu:16.04

# Build dependencies
RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted" >> /etc/apt/sources.list && apt-get update && apt-get install -y wget git mercurial libgoogle-perftools-dev libsparsehash-dev libboost-all-dev autoconf libtool python python-pip
RUN apt-get build-dep -y cmake
RUN pip install cython numpy

# CMake 3.8.2
RUN cd /opt && \
        wget "https://cmake.org/files/v3.8/cmake-3.8.2.tar.gz" && \
        tar xf cmake-3.8.2.tar.gz && \
        cd cmake-3.8.2 && \
        ./configure && \
        make -j 2 install

# Eigen, version 3.3.4
ENV EIGEN_VERSION 3.3.4
RUN cd /opt && \
        hg clone https://bitbucket.org/eigen/eigen/ && \
        cd eigen && \
        hg update -r ${EIGEN_VERSION}
