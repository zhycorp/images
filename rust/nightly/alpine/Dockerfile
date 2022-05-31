# TAGS: nightly
# VARIANT: alpine-ptero
# PLATFORMS: linux/amd64, linux/arm64/v8
FROM rustlang/rust:nightly-alpine

WORKDIR /app

RUN apk add --no-cache --update \
        git curl iproute2 gcc g++ musl-dev cmake make clang lld bash \
    && adduser -D -h /home/container container 

USER container
ENV USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo
WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
