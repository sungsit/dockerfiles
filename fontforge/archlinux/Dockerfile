#
# FontForge (on Archlinux)
#

FROM nfnty/arch-mini

MAINTAINER Sungsit Sawaiwan
ENV version=20150719 user=fontdev

# Change mirrors, sync & install required packages
#COPY config/mirrorlist /etc/pacman.d/
RUN pacman -Syy --noc && pacman -S --noc sudo fontforge bdf-unifont

# Add fontdev user & password-less sudoer
ENV home=/home/$user \
    sudofile=/etc/sudoers.d/$user \
    srcdir=/home/$user/src
RUN useradd --create-home --home-dir $home $user && \
    echo $user " ALL=(ALL:ALL) NOPASSWD:ALL" > $sudofile && \
    chmod 600 $sudofile

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
# docker build -t "sungsit/fontforge:archlinux" .
#
