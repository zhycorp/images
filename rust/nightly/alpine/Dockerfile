# TAGS: nightly
# VARIANT: alpine-ptero
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM alpine:3.16.0

WORKDIR /app

ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH

RUN apk add --no-cache --update \
        ca-certificates git curl iproute2 gcc g++ musl-dev cmake make clang lld bash \
    && adduser -D -h /home/container container 

RUN set -eux; \
    apkArch="$(apk --print-arch)"; \
    case "$apkArch" in \
        x86_64) rustArch='x86_64-unknown-linux-musl' ;; \
        aarch64) rustArch='aarch64-unknown-linux-musl' ;; \
        *) echo >&2 "unsupported architecture: $apkArch"; exit 1 ;; \
    esac; \
    \
    url="https://static.rust-lang.org/rustup/dist/${rustArch}/rustup-init"; \
    wget "$url"; \
    chmod +x rustup-init; \
    ./rustup-init -y --no-modify-path --default-toolchain nightly --profile minimal --component rust-src --default-toolchain nightly -y; \
    rm rustup-init; \
    chmod -R a+w $RUSTUP_HOME $CARGO_HOME; \
    rustup --version; \
    cargo --version; \
    rustc --version;

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
