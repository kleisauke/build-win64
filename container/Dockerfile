FROM ubuntu:xenial
MAINTAINER Lovell Fuller <npm@lovell.info>

# basic stuff
RUN \
  echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | debconf-set-selections && \
  dpkg --add-architecture i386 && \
  apt-get update && \
  apt-get install -y \
    build-essential \
    jhbuild \
    libtool \
    intltool \
    mingw-w64 \
    mingw-w64-tools \
    nasm \
    cmake 

# needed packages for master build
RUN \
  apt-get install -y \
    libxml2-dev \
    libexpat1-dev \
    glib2.0-dev \
    libglib2.0-dev \
    gobject-introspection \
    python-gi-dev \
    libgirepository1.0-dev \
    swig

# strange extras for certain packages
# croco needs gtk-doc
# we use wine to test the build
RUN \
  apt-get install -y \
    gtk-doc-tools \
    xmlto \
    wget \
    yelp-tools \
    gperf \
    wine \
    wine1.6-amd64

# Create a default, non-root 'build' user
RUN groupadd -r build && useradd -m -g build build
WORKDIR /data
USER build
