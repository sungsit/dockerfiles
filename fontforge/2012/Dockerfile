#
# FontForge (2012 + Python Extension)
# Sometimes I need older FontForge to test some fonts.
#

FROM debian:8.1

MAINTAINER Sungsit Sawaiwan

# Install minimal packages:
# `ttf-unifonts` pkg is required for displaying unicode glyphs 
RUN apt-get -y update && \
    apt-get -y --no-install-recommends install \
      fontforge \
      python-fontforge \
      ttf-unifont

# Cleanup
RUN rm -rf /var/lib/apt/lists/*

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
# docker build -t "sungsit/fontforge:2012" .
#
