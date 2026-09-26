FROM        --platform=$TARGETOS/$TARGETARCH valkey/valkey:9.1-trixie

LABEL       org.opencontainers.image.source="https://github.com/EmpireWar/yolks"
LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

ENV         DEBIAN_FRONTEND=noninteractive

RUN         apt-get update -y \
            && apt-get install -y --no-install-recommends iproute2 tini \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -d /home/container -m container -s /bin/bash

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL  SIGINT

COPY        --chmod=755 ./entrypoint.sh /entrypoint.sh
ENTRYPOINT  ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
