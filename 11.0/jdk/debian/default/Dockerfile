FROM nicoherbigde/debian:buster

LABEL maintainer="Nico Herbig <nico@nicoherbig.io>"


# Install Adopt Open Java Development Kit (AdoptOpenJDK)

ARG JAVA_DOWNLOAD_URL=https://github.com/AdoptOpenJDK/openjdk11-binaries/releases/download/jdk-11.0.9%2B11.1/OpenJDK11U-jdk_x64_linux_hotspot_11.0.9_11.tar.gz

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
