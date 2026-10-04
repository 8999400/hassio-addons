ARG BUILD_FROM=debian:bookworm-slim
FROM ${BUILD_FROM}

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Minsk

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    wget \
    ffmpeg \
    libfontconfig1 \
    && rm -rf /var/lib/apt/lists/*

RUN wget --user-agent="Mozilla/5.0" -O /tmp/emby.deb "https://get.starmedia.workers.dev/dl/download-latest/server?beta=true&match=emby-server-deb_%2C_amd64.deb" \
    && (dpkg -i /tmp/emby.deb || apt-get install -f -y) \
    && rm /tmp/emby.deb

EXPOSE 8096

CMD ["/opt/emby-server/bin/emby-server"]
