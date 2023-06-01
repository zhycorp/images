# TAGS: current, latest
# VARIANT:
# PLATFORMS: linux/amd64, linux/arm64/v8, linux/arm/v7, linux/ppc64le, linux/s390x
FROM docker.io/library/node:19.9.0-slim

LABEL author="Frutbits Indonesia" maintainer="support@frutbits.org"

ARG BUILDPLATFORM

WORKDIR /app

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        iputils-ping \
        procps \
        tini \
        tzdata \
        curl \
        ffmpeg \
        git \
        openssl \
        sqlite3 \
        tar \
    && apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false \
    && apt-get autoremove -y \
    && apt-get autoclean -y \
    && rm -rf /var/lib/apt/lists/* \
    && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ../../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]