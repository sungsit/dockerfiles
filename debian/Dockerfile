#
# Debian Thai mirror containers
#

FROM debian:8.1

# Change mirror
RUN sed -i "s/httpredir.debian.org/mirror1.ku.ac.th/" /etc/apt/sources.list

#
# Build command:
# docker build -t "sungsit/debian:thai-mirror" .
#
# Test command:
# docker run -it --rm "sungsit/debian:thai-mirror" echo "Hello Debian (thai-mirror)!"
#
