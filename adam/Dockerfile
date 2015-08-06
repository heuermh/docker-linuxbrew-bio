FROM heuermh/apache-spark
MAINTAINER Michael Heuer <heuermh@acm.org>

# see https://github.com/bigdatagenomics/adam/issues/747
# RUN brew tap homebrew/science
# RUN brew install adam

RUN brew install maven \
  && cd /home/linuxbrew \
  && git clone https://www.github.com/bigdatagenomics/adam.git \
  && cd adam \
  && mvn clean package -DskipTests

ENV PATH /home/linuxbrew/adam/bin:$PATH
