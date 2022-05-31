# TAGS: nightly
# VARIANT: alpine-ptero
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM rustlang/rust:nightly-alpine

WORKDIR /app

ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH

RUN apk add --no-cache --update \
        ca-certificates git curl iproute2 gcc g++ musl-dev cmake make clang lld bash \
    && rustup component add rust-src --toolchain nightly-x86_64-unknown-linux-gpu \
    && adduser -D -h /home/container container 

USER container

ENV USER=container \
    HOME=/home/container 

WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh

CMD ["/bin/bash", "/entrypoint.sh"]
