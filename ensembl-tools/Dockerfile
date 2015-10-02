#FROM sjackman/linuxbrew
FROM ubuntu
MAINTAINER Michael Heuer <heuermh@acm.org>

#RUN brew tap homebrew/science \
#  && brew install ensembl-tools

RUN apt-get update && apt-get install -y \
  wget \
  libwww-perl \
  libarchive-zip-perl \
  libdbd-mysql-perl \
  libjson-perl

RUN mkdir /opt/ensembl-tools
WORKDIR /opt/ensembl-tools

RUN wget https://github.com/Ensembl/ensembl-tools/archive/release/82.tar.gz && \
  tar --strip-components=2 -xzf 82.tar.gz && \
  cd variant_effect_predictor && \
  perl INSTALL.pl --AUTO a --SPECIES homo_sapiens --ASSEMBLY GRCh38 --NO_HTSLIB
#  perl INSTALL.pl --AUTO acf --SPECIES homo_sapiens --ASSEMBLY GRCh38 --NO_HTSLIB

ENV PERL5LIB "$PERL5LIB:/opt/ensembl-tools/variant_effect_predictor"

ENTRYPOINT ["perl", "/opt/ensembl-tools/variant_effect_predictor/variant_effect_predictor.pl"]
