FROM golang:1.17

WORKDIR /app

ENV PROTOC_VERSION=3.17.2

ARG ARC

RUN if [ "$ARC" = "arm" ]; then export PKG=aarch_64; else export PKG=x86_64; fi \
    && apt-get update \
    && apt-get install -y unzip \
    && rm -rf /var/lib/apt/lists/* \
    && wget https://github.com/protocolbuffers/protobuf/releases/download/v${PROTOC_VERSION}/protoc-${PROTOC_VERSION}-linux-${PKG}.zip \
    && unzip protoc-${PROTOC_VERSION}-linux-${PKG}.zip \
    && mv -v bin/* /usr/bin/  \
    && mv -v include/* /usr/include/  \
    && rm -r bin include protoc-${PROTOC_VERSION}-linux-${PKG}.zip \
    && go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.26.0