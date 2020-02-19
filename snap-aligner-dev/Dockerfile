FROM ubuntu
LABEL maintainer="heuermh@acm.org"

RUN apt-get update && apt-get install -y build-essential git zlib1g-dev

WORKDIR /opt
RUN git clone https://github.com/amplab/snap.git snap-aligner

WORKDIR /opt/snap-aligner
RUN make

ENV PATH="/opt/snap-aligner:${PATH}"
CMD ["/opt/snap-aligner/snap-aligner"]
