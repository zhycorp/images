# TAGS: nightly
# VARIANT: ptero
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM alpine:3.16.0

WORKDIR /app

RUN apt-get update \
    && apt-get -y install git curl iproute2 gcc g++ musl-dev cmake make clang lld \
    && adduser -D -h /home/container container \
    && curl -sSf https://sh.rustup.rs | sh -s -- --profile minimal --component rust-src --default-toolchain nightly -y

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
