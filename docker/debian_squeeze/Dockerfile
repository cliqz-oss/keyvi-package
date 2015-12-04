FROM debian:squeeze

RUN apt-get update && \
    apt-get install -y \
      build-essential \
      devscripts \
      wget \
      gcc \
      m4 \
      libgmp3-dev \
      libmpfr-dev \
      linux-libc-dev \
      libc6-dev-i386 \
      libc6-dev \
      zlib1g-dev \
      bison \
      libbz2-dev \
      libicu-dev \
      libssl-dev \
      libdb-dev \
      libsqlite3-dev \
      libncurses5-dev \
      libgdbm-dev \
      libreadline5-dev

# Install backports
RUN echo 'deb http://http.debian.net/debian-backports squeeze-backports main' > /etc/apt/sources.list.d/squeeze-backports.list && \
    apt-get update

# install some tools from backports
RUN apt-get -t squeeze-backports install -y debhelper cmake

# create work directory
RUN mkdir /work

# install python 2.7
RUN cd /work && wget http://www.python.org/ftp/python/2.7.10/Python-2.7.10.tgz
RUN cd /work && tar -xzf Python-2.7.10.tgz
RUN cd /work/Python-2.7.10 && ./configure --enable-shared && make && make install
RUN update-alternatives --install /usr/bin/python python /usr/bin/python2.6 20
RUN update-alternatives --install /usr/bin/python python /usr/local/bin/python2.7 50
RUN update-alternatives --set python /usr/bin/python2.6
RUN ldconfig

# get tool-chain
RUN mkdir /work/gcc
COPY bld.sh /work/gcc/bld.sh
RUN cd /work/gcc && ./bld.sh

# get keyvi
RUN cd /work && git clone https://github.com/cliqz-oss/keyvi

# install more pre-requisites
RUN apt-get install -y scons

# upgrade pip
RUN cd /work && wget https://bootstrap.pypa.io/get-pip.py --no-check-certificate && python get-pip.py
