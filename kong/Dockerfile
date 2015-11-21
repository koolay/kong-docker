FROM phusion/baseimage
MAINTAINER KOOLAY
ENV KONG_VERSION 0.5.3

RUN apt-get update
RUN apt-get install -y netcat lua5.1 openssl libpcre3 dnsmasq wget \
     && apt-get clean

RUN cd /tmp/ && wget https://github.com/Mashape/kong/releases/download/0.5.3/kong-0.5.3.trusty_all.deb \
    && dpkg -i kong-$KONG_VERSION.trusty_all.deb \
    #rm kong*.deb

ADD start.sh /

VOLUME ["/etc/kong/"]
ENTRYPOINT ["/start.sh"]
