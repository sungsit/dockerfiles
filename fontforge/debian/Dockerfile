#
# FontForge (2012 + Python Extension)
# Sometimes I need older FontForge to test some fonts.
#

FROM debian:8.1
#FROM sungsit/debian:thai-mirror

MAINTAINER Sungsit Sawaiwan

ENV user=fontdev
ENV home=/home/$user \
    sudofile=/etc/sudoers.d/$user

# Install minimal packages:
RUN apt-get -y update \
&&  apt-get -y --no-install-recommends install \
    fontforge \
    python-fontforge \
    sudo \
    ttf-unifont \

# Add fontdev user & password-less sudoer \
&&  useradd --create-home --home-dir $home $user \
&&  echo $user " ALL=(ALL:ALL) NOPASSWD:ALL" > $sudofile \
&&  chmod 600 $sudofile \
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
# docker build -t "sungsit/fontforge:debian" .
#
