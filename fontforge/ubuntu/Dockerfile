#
# FontForge (Ubuntu PPA + Python Extension)
#

FROM ubuntu:14.10
#FROM sungsit/ubuntu:thai-mirror

MAINTAINER Sungsit Sawaiwan

ENV user=fontdev
ENV home=/home/$user \
    sudofile=/etc/sudoers.d/$user

# Required for `add-apt-repository` \
RUN apt-get -y update \
&&  apt-get -y --no-install-recommends install \
    python-software-properties \
    software-properties-common \
    sudo \

# Add FontForge PPA \
&&  add-apt-repository -y ppa:fontforge/fontforge \
&&  apt-get -y update \

# Install minimal packages: \
# `ttf-unifonts` pkg is required for displaying unicode glyphs \
&&  apt-get -y --no-install-recommends install \
    fontforge \
    python-fontforge \
    ttf-unifont \

# Add fontdev user & password-less sudoer \
&&  useradd --create-home --home-dir $home $user \
&&  echo $user " ALL=(ALL:ALL) NOPASSWD:ALL" > $sudofile \
&&  chmod 600 $sudofile \

# Cleanup \
&&  apt-get -y autoremove \
    python-software-properties \
    software-properties-common \
&&  rm -rf /var/lib/apt/lists/*

# Copy config files
COPY config/local.conf /etc/fonts/
COPY config/.bashrc $home/

RUN chown -R $user:$user $home

# Set default command & working dir for fontdev user.
USER $user
WORKDIR $home
CMD [ "fontforge" ]

#
# Build command:
# docker build -t "sungsit/fontforge:ubuntu" .
#
