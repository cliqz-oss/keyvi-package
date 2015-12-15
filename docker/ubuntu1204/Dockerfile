FROM ubuntu:12.04

RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y software-properties-common python-software-properties


RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test
RUN add-apt-repository -y ppa:boost-latest/ppa

RUN apt-get update && \
    apt-get install -y \
      build-essential \
      gcc-4.8 \
      g++-4.8 \
      clang \
      scons \
      valgrind \
      cmake \
      libboost-thread1.55-dev \
      libboost-system1.55-dev \
      libboost-test1.55-dev \
      libboost1.55-dev \
      libboost-date-time1.55-dev \
      libboost-regex1.55-dev \
      libboost-filesystem1.55-dev \
      libboost-program-options1.55-dev \
      libboost-iostreams1.55-dev \
      libsnappy-dev \
      zlib1g-dev \
      doxygen \
      libstdc++-4.8-dev \
      python-dev \
      python-setuptools \
      cython \
      python-pip

# create work directory
RUN mkdir /work

RUN apt-get install -y git

RUN pip install pytest

RUN pip install msgpack-python

RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 40 --slave /usr/bin/g++ g++ /usr/bin/g++-4.8

# get keyvi
RUN cd /work && git clone https://github.com/cliqz-oss/keyvi


