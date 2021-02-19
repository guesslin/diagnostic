FROM alpine:3.13

LABEL maintainer=guesslin1986@gmail.com

RUN apk update && apk add --no-cache bcc-tools bcc-doc bash iproute2 tcpdump python3

COPY __init__.py /usr/lib/python3.8/site-packages/bcc/__init__.py

ENV PATH="/usr/share/bcc/tools:${PATH}"
ENTRYPOINT /bin/bash
