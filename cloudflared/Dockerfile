# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Install cloudflared
ARG BUILD_ARCH
RUN \
    case "${BUILD_ARCH}" in \
        amd64) ARCH="amd64" ;; \
        aarch64) ARCH="arm64" ;; \
    esac \
    && curl -sSLf -o /usr/local/bin/cloudflared \
        "https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-${ARCH}" \
    && chmod +x /usr/local/bin/cloudflared \
    && /usr/local/bin/cloudflared --version

# Copy root filesystem
COPY rootfs /
