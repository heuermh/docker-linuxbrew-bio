FROM sjackman/linuxbrew
MAINTAINER Michael Heuer <heuermh@acm.org>

USER root
RUN apt-get update && apt-get install -y \
  python-setuptools

USER linuxbrew
RUN brew tap homebrew/science \
  && brew install freebayes
