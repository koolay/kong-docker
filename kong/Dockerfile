FROM phusion/baseimage
MAINTAINER KOOLAY
ENV KONG_VERSION 0.5.3

RUN apt-get update
RUN apt-get install -y netcat lua5.1 openssl libpcre3 dnsmasq wget \
     && apt-get clean

COPY start.sh /start.sh
COPY kong.yml /etc/kong/kong.yml
RUN chmod +x /start.sh

RUN cd /tmp/ && wget https://github.com/Mashape/kong/releases/download/$KONG_VERSION/kong-$KONG_VERSION.trusty_all.deb \
    && dpkg -i kong-$KONG_VERSION.trusty_all.deb \
    && rm kong*.deb

VOLUME ["/etc/kong/"]
ENTRYPOINT ["/start.sh"]
