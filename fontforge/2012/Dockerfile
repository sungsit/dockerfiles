#
# FontForge 2012 container
# Sometimes I need older FontForge to test my fonts.
#

# To use Debian official image, change to `FROM debian:8.1` 
FROM sungsit/debian:thai-mirror
MAINTAINER Sungsit Sawaiwan

# Install minimal packages
RUN apt-get -y update && \
    apt-get -y --no-install-recommends install sudo \
    fontforge python-fontforge ttf-unifont && \
    rm -rf /var/cache/apt/* /var/lib/apt/lists/*

# Basic fontfonfig
COPY local.conf /etc/fonts/local.conf

# Add fontdev user
ENV USER=fontdev HOME=/home/$USER
RUN useradd --create-home --home-dir $HOME $USER && \
    chown -R $USER:$USER $HOME

USER $USER
WORKDIR $HOME

ENTRYPOINT [ "fontforge" ]

#
# Build command:
# docker build -t "sungsit/fontforge:2012" .
#
# Test command: Mount Unix socket
#
# Linux host
# docker run -it --rm -e DISPLAY=unix$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix "sungsit/fontforge:2012"
#
# Mac host, see https://github.com/docker/docker/issues/8710#issuecomment-71113263
#
