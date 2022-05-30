# TAGS: stable
# VARIANT:
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM rust:1.61.0-alpine

WORKDIR /app

RUN apk add --no-cache --update \
        git curl iproute2 bash \
    && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]