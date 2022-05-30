# TAGS: stable
# VARIANT:
# PLATFORMS: linux/amd64, linux/arm64/v8, linux/arm/v7, linux/i386
FROM rust:1.61.0-alpine

WORKDIR /app

RUN apk add --no-cache --update \
        bash iproute2 git sqlite sqlite-dev \
        zip tar curl g++ make \
    && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]