# TAGS: nightly
# VARIANT: alpine-ptero
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM --platform=$BUILDPLATFORM docker.io/library/alpine:edge

ARG BUILDPLATFORM

WORKDIR /app

ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH

RUN apk add --no-cache --update \
        git curl iproute2 gcc g++ musl-dev cmake make clang lld bash \
    && curl -sSf https://sh.rustup.rs | sh -s -- --profile minimal --component rust-src --default-toolchain nightly -y \
    && if [ "$BUILDPLATFORM" == "linux/amd64" ]; then export TOOLCHAIN=nightly-x86_64-unknown-linux-musl; \
        else export TOOLCHAIN=nightly-aarch64-unknown-linux-musl; fi \
    && rustup toolchain install $TOOLCHAIN \
    && rustup component add rust-src --toolchain $TOOLCHAIN \
    && adduser -D -h /home/container container 

USER container

ENV USER=container \
    HOME=/home/container \
    CARGO_HOME=/home/container/.cargo

WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh

CMD ["/bin/bash", "/entrypoint.sh"]
