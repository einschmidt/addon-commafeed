ARG BUILD_FROM
FROM $BUILD_FROM

# Copy root filesystem
COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# https://github.com/Athou/commafeed/releases
ENV COMMAFEED_VERSION 2.5.0

# Install Java
RUN set -eux; \
	apk add openjdk8=8.252.09-r0 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community

# Install CommaFeed
RUN set -eux; \
	mkdir -p /commafeed; \
    curl -J -L -o /commafeed/commafeed.jar "https://github.com/Athou/commafeed/releases/download/${COMMAFEED_VERSION}/commafeed.jar"

EXPOSE 8082

# Labels
LABEL \
    io.hass.name="CommaFeed" \
    io.hass.description="Google Reader inspired self-hosted RSS reader." \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Einschmidt" \
    org.label-schema.description="CommaFeed add-on by Einschmidt" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="CommaFeed" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://github.com/einschmidt/hassio-addons" \
    org.label-schema.usage="https://github.com/einschmidt/hassio-addons/blob/master/commafeed/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/einschmidt/hassio-addons" \
    org.label-schema.vendor="Einschmidt"
