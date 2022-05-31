# TAGS: nightly
# VARIANT: ptero
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM --platform=$BUILDPLATFORM rustlang/rust:nightly-slim

ARG BUILDPLATFORM

WORKDIR /app

RUN apt-get update \
    && apt-get -y install git curl iproute2 gcc g++ musl-dev cmake make clang lld libc6-dev \
    && if [ "$BUILDPLATFORM" == "linux/amd64" ]; then export TOOLCHAIN=nightly-x86_64-unknown-linux-gnu; \
        else export TOOLCHAIN=aarch64-unknown-linux-gnu; fi \
    && rustup toolchain install $TOOLCHAIN \
    && rustup component add rust-src --toolchain $TOOLCHAIN \
    && adduser -D -h /home/container container 

USER container

ENV USER=container \
    HOME=/home/container CARGO_HOME=/home/container/.cargo
    
WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
