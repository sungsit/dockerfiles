#
# FontForge (PPA + Python Extension)
#

FROM ubuntu:14.10

MAINTAINER Sungsit Sawaiwan

# Required for `add-apt-repository`
RUN apt-get -y update && \
    apt-get -y --no-install-recommends install \
      python-software-properties \
      software-properties-common

# Add FontForge PPA
RUN add-apt-repository -y ppa:fontforge/fontforge && \
    apt-get -y update

# Install minimal packages:
# `ttf-unifonts` pkg is required for displaying unicode glyphs
RUN apt-get -y --no-install-recommends install \
      fontforge \
      python-fontforge \
      ttf-unifont

# Cleanup
RUN apt-get -y autoremove \
      python-software-properties \
      software-properties-common && \ 
    rm -rf /var/lib/apt/lists/*

# Basic fontfonfig
COPY local.conf /etc/fonts/local.conf

# Add fontdev user
ENV USER=fontdev HOME=/home/fontdev
RUN useradd --create-home --home-dir $HOME $USER && \
    chown -R $USER:$USER $HOME

# Set default command & working dir for fontdev user.
USER $USER
WORKDIR $HOME
CMD [ "fontforge" ]

#
# Build command:
# docker build -t "sungsit/fontforge:ppa" .
#
