FROM sjackman/linuxbrew
MAINTAINER Michael Heuer <heuermh@acm.org>

USER root
RUN apt-get update && apt-get install -y \
    libboost-all-dev \
    python-setuptools

USER linuxbrew
RUN brew tap homebrew/science \
    && brew install bamtools \
    && brew install bwa \
    && brew install samtools

USER root
RUN mkdir /opt/mhc-prg \
    && cd /opt/mhc-prg \
    && mkdir bin \
    && mkdir obj \
    && mkdir tmp \
    && mkdir tmp/hla \
    && mkdir tmp2 \
    && mkdir tmp2/GS_nextGen \
#
#   todo: && mkdir /opt/mhc-prg/tmp2/GS_nextGen/${graph directory symlink} \
    && git clone https://github.com/AlexanderDilthey/MHC-PRG.git src \
#
#   todo: header in bamtools utils is not present in bamtools/include/bamtools, grab source
    && cd /home/linuxbrew/.linuxbrew/opt/bamtools \
    && git clone https://github.com/pezmaster31/bamtools.git

# todo: replace paths in LIB_BOOST, INCS, and LIBS in makefile
#
# LIB_BOOST (remove line)
# INCS = -IGraph -I/home/linuxbrew/.linuxbrew/opt/bamtools/include/bamtools -I/home/linuxbrew/.linuxbrew/opt/bamtools/bamtools/src
# LIBS = /home/linuxbrew/.linuxbrew/opt/bamtools/lib/libbamtools.a /home/linuxbrew/.linuxbrew/opt/bamtools/lib/libbamtools-utils.so

#RUN cd /opt/mhc-prg/src \
#    && make all

USER linuxbrew

ENV $PATH /opt/mhc-prg/src:/opt/mhc-prg/bin:$PATH
