FROM ubuntu:bionic AS builder

LABEL maintainer="guesslin1986@gmail.com"

RUN apt-get update && \
    apt-get install -y libpcap-dev libnl-3-dev libnl-genl-3-dev binutils-dev libreadline6-dev autoconf libtool pkg-config build-essential git man

WORKDIR /tmp/
RUN git clone https://github.com/nhorman/dropwatch && \
    cd dropwatch && \
    ./autogen.sh && \
    ./configure && \
    make && \
    make install && \
    cd ../ && \
    rm -rf dropwatch

WORKDIR /
CMD /bin/bash

# =========================================================
FROM ubuntu:bionic AS final

LABEL maintainer="guesslin1986@gmail.com"

RUN apt-get update && \
    apt-get install -y libpcap-dev libnl-3-dev libnl-genl-3-dev binutils-dev libreadline6-dev man

COPY --from=builder /usr/local/bin/dropwatch /usr/local/bin/

WORKDIR /
CMD /bin/bash
