# TAGS: current, latest
# VARIANT: alpine
# PLATFORMS: linux/amd64, linux/arm64/v8, linux/arm/v7, linux/arm/v6, linux/ppc64le, linux/s390x
FROM docker.io/library/node:18.10.0-alpine

LABEL author="Frutbits Indonesia" maintainer="support@frutbits.org"

ARG BUILDPLATFORM

WORKDIR /app

RUN apk add --no-cache \
    tini \
    tzdata \
    ca-certificates curl ffmpeg git openssl sqlite tar tzdata \
    && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh
CMD ["/bin/ash", "/entrypoint.sh"]