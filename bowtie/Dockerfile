FROM linuxbrew/linuxbrew
MAINTAINER Michael Heuer <heuermh@acm.org>

USER root
RUN apt-get update && apt-get install -y \
  python

USER linuxbrew
RUN brew tap homebrew/science \
  && brew install bowtie
