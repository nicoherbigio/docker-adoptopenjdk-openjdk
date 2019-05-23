FROM nicoherbigio/debian:stretch

LABEL maintainer="Nico Herbig <nico@nicoherbig.io>"


# Install Adopt Open Java Development Kit (AdoptOpenJDK)

ARG JAVA_VERSION=jdk-11.0.3%2B7
ARG JAVA_DOWNLOAD_URL=https://api.adoptopenjdk.net/v2/binary/releases/openjdk11?os=linux&arch=x64&release=${JAVA_VERSION}&type=jdk&openjdk_impl=hotspot&heap_size=normal

ARG JAVA_INSTALL_DIR=/opt/java/openjdk

RUN set -ex \
    && apt-get update \
    && apt-get install -y --no-install-recommends curl ca-certificates \
    && mkdir -p ${JAVA_INSTALL_DIR} \
    && curl -fSL ${JAVA_DOWNLOAD_URL} | tar -xz --no-same-owner --strip-components=1 -C ${JAVA_INSTALL_DIR} \
    && apt-get remove -y curl ca-certificates \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=${JAVA_INSTALL_DIR}
ENV PATH="${JAVA_INSTALL_DIR}/bin:${PATH}"
ENV JAVA_TOOL_OPTIONS="-XX:+UseContainerSupport"
