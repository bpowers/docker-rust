FROM debian:stretch
MAINTAINER Bobby Powers "bobbypowers@gmail.com"

ENV DEBIAN_FRONTEND=noninteractive

RUN \
  apt-get update -qq -y && \
  apt-get upgrade -qq -y && \
  apt-get install -qq -y --no-install-recommends \
    ca-certificates \
    curl \
    software-properties-common \
    vim \
    emacs-nox \
    less \
    htop \
    man \
    lsb-release \
    build-essential \
    make \
    git \
    z3 \
    python-all && \
  rm -rf /var/lib/apt/lists/*

ENV RUST_ARCHIVE=rust-nightly-x86_64-unknown-linux-gnu.tar.gz
ENV RUST_DOWNLOAD_URL=https://static.rust-lang.org/dist/$RUST_ARCHIVE

RUN mkdir /rust
WORKDIR /rust

RUN curl -fsOSL $RUST_DOWNLOAD_URL \
    && curl -s $RUST_DOWNLOAD_URL.sha256 | sha256sum -c - \
    && tar -C /rust -xzf $RUST_ARCHIVE --strip-components=1 \
    && rm $RUST_ARCHIVE \
    && ./install.sh
