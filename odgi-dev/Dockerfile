# load base image
FROM ubuntu:18.04

# update system
RUN apt-get update

# install dependencies
RUN apt-get -qqy install git zlib1g zlib1g-dev libomp-dev

# install build tools
RUN apt-get -qqy install build-essential software-properties-common python3-dev python3-distutils && \
    add-apt-repository -y ppa:ubuntu-toolchain-r/test && \
    apt-get update > /dev/null && \
    apt-get -qqy install gcc-snapshot && \
    apt-get update > /dev/null && \
    apt-get -qqy install gcc-8 g++-8 && \
    update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 80 --slave /usr/bin/g++ g++ /usr/bin/g++-8 && \
    apt-get -qqy install cmake git

# copy over current directory to container
RUN git clone --recursive https://github.com/vgteam/odgi.git

# set working directory
WORKDIR odgi

# build
RUN cmake -H. -Bbuild && cmake --build build -- -j 3

# cleanup
RUN apt-get -qy autoremove

# add odgi to the PATH
ENV PATH /odgi/bin:$PATH
