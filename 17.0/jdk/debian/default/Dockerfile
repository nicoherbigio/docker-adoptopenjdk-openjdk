FROM nicoherbigde/debian:bullseye

LABEL maintainer="Nico Herbig <nico@nicoherbig.io>"


# Install Eclipse Temurin Open Java Development Kit (Eclipse Temurin OpenJDK)

ARG JAVA_DOWNLOAD_URL=https://github.com/adoptium/temurin17-binaries/releases/download/jdk-17.0.5%2B8/OpenJDK17U-jdk_x64_linux_hotspot_17.0.5_8.tar.gz

ARG JAVA_INSTALL_DIR=/opt/java/openjdk

RUN set -euxo \
    && apt-get update \
    && apt-get install -y --no-install-recommends curl ca-certificates fontconfig \
    && mkdir -p ${JAVA_INSTALL_DIR} \
    && curl -fSL ${JAVA_DOWNLOAD_URL} | tar -xz --no-same-owner --strip-components=1 -C ${JAVA_INSTALL_DIR} \
    && apt-get remove -y curl ca-certificates \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=${JAVA_INSTALL_DIR}
ENV PATH="${JAVA_INSTALL_DIR}/bin:${PATH}"
