FROM        --platform=$TARGETOS/$TARGETARCH valkey/valkey:9.1-alpine

LABEL       org.opencontainers.image.source="https://github.com/EmpireWar/yolks"
LABEL       author="Empire War Admins" maintainer="admin@empirewar.org"

RUN         apk add --no-cache tini \
            && adduser -D -h /home/container -s /bin/sh container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL  SIGINT

COPY        --chmod=755 ./entrypoint.sh /entrypoint.sh
ENTRYPOINT  ["/sbin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
