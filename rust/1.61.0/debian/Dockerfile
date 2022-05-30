# TAGS: stable
# VARIANT:
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM rust:1.61.0-slim

WORKDIR /app

RUN apt-get update \
    && apt-get -y install git dnsutils curl iproute2 ffmpeg \
    && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
