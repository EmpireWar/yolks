FROM        --platform=$TARGETOS/$TARGETARCH eclipse-temurin:25.0.5_8-jdk-noble

LABEL       org.opencontainers.image.source="https://github.com/EmpireWar/yolks"
LABEL       author="Empire War Admins" maintainer="admin@empirewar.org"

ENV         DEBIAN_FRONTEND=noninteractive

RUN         apt update -y \
            && apt install -y curl lsof ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2 libfreetype6 tini zip unzip \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -m -d /home/container -s /bin/bash container

# ponytail: CVE-2026-114938 "java4shell". Swaps in the patched 25.0.5.1+2 JDK
# until Docker Hub publishes it; then switch FROM to
# eclipse-temurin:25-jdk-noble and delete this block.
RUN         curl -fsSL -o /tmp/jdk.tar.gz https://github.com/adoptium/temurin25-binaries/releases/download/jdk-25.0.5.1%2B2/OpenJDK25U-jdk_x64_linux_hotspot_25.0.5.1_2.tar.gz \
            && echo "760f91b22c3efc9bd1b64ff950598231be82928cc807e30691a0e7a2995a62c0  /tmp/jdk.tar.gz" | sha256sum -c - \
            && rm -rf "$JAVA_HOME"/* \
            && tar -xzf /tmp/jdk.tar.gz -C "$JAVA_HOME" --strip-components=1 \
            && rm /tmp/jdk.tar.gz \
            && java -version

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL  SIGINT

COPY        --chmod=755 ./entrypoint.sh /entrypoint.sh
ENTRYPOINT  ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
