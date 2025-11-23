# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Install cloudflared
ARG BUILD_ARCH
RUN \
    apk add --no-cache dpkg \
    && case "${BUILD_ARCH}" in \
        amd64) \
            curl -sSLf -o cloudflared.deb \
                "https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb" \
            ;; \
        aarch64) \
            curl -sSLf -o cloudflared.deb \
                "https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm64.deb" \
            ;; \
    esac \
    && dpkg -x cloudflared.deb /tmp/cloudflared \
    && mv /tmp/cloudflared/usr/bin/cloudflared /usr/local/bin/cloudflared \
    && chmod +x /usr/local/bin/cloudflared \
    && rm -rf cloudflared.deb /tmp/cloudflared \
    && apk del dpkg \
    && /usr/local/bin/cloudflared --version

# Copy root filesystem
COPY rootfs /
