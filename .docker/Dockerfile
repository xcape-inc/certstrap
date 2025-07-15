ARG BASE_IMAGE=alpine
ARG BASE_IMAGE_VERSION=3.16
FROM ${BASE_IMAGE}:${BASE_IMAGE_VERSION}
RUN apk add libc6-compat tzdata
ARG TARGETOS
ARG TARGETARCH
COPY certstrap-*-${TARGETOS}-${TARGETARCH} /usr/bin/
RUN addgroup -g 1000 certstrap \
    && adduser certstrap -u 100 -G certstrap -s /bin/sh -S \
    && chmod 755 /usr/bin/certstrap-*-${TARGETOS}-${TARGETARCH} \
    && ln -s /usr/bin/certstrap-*-${TARGETOS}-${TARGETARCH} /usr/bin/certstrap
WORKDIR /home/certstrap
USER certstrap
RUN mkdir /home/certstrap/workdir
RUN mkdir /home/certstrap/workdir2
ENTRYPOINT ["/usr/bin/certstrap"]
