#
# Debian Thai mirror containers
#

FROM debian:8.1
MAINTAINER Sungsit Sawaiwan

# Change mirror & update
ENV mirror=http://mirror1.ku.ac.th/debian/ dist=jessie compo="main" list=/etc/apt/sources.list

RUN echo "deb ${mirror} ${dist} ${compo}" > ${list} && \
    echo "deb ${mirror} ${dist}-updates $compo" >> ${list} && \
    echo "deb http://security.debian.org/ ${dist}/updates ${compo}" >> ${list} && \
    apt-get -y update && apt-get -y upgrade && \
    rm -rf /var/cache/apt/* /var/lib/apt/lists/*

#
# Build command:
# docker build -t "sungsit/debian:thai-mirror" .
#
# Test command:
# docker run -it --rm "sungsit/debian:thai-mirror" echo "Hello Debian (thai-mirror)!"
#
