# TAGS: stable
# VARIANT: ptero
# PLATFORMS: linux/amd64, linux/arm64/v8

FROM  --platform=$BUILDPLATFORM eqalpha/keydb

LABEL   author="Frutbis Indonesia" maintainer="support@frutbits.org"

ENV     DEBIAN_FRONTEND noninteractive

RUN     apt -y update && \
        apt -y upgrade && \
        apt -y install iproute2 && \
        useradd -d /home/container -m container -s /bin/bash

USER    container
ENV     USER=container HOME=/home/container
WORKDIR /home/container

COPY    ./entrypoint.sh /entrypoint.sh
CMD     ["/bin/bash", "/entrypoint.sh"]