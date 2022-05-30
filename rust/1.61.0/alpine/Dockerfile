# TAGS: stable
# VARIANT:
# PLATFORMS: linux/amd64, linux/arm64/v8, linux/arm/v7, linux/ppc64le, linux/s390x
FROM rust:1.61.0-alpine

WORKDIR /app

RUN apk add --no-cache --update \
        bash iproute git sqlite sqlite-dev \
        python3 python3-dev ca-certificates tzdata \
        zip tar curl g++ make \
    && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../entrypoint.sh /entrypoint.sh

