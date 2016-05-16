FROM mhart/alpine-node
MAINTAINER koolay

ENV DASHBOARD_VERSION 1.1.2

RUN mkdir /data && cd /data \
    && wget https://github.com/PGBI/kong-dashboard/archive/v{$DASHBOARD_VERSION}.tar.gz && tar -xf  v{$DASHBOARD_VERSION }.tar.gz \
    && cd kong-dashboard-{$DASHBOARD_VERSION } && rm -rf archive/v{$DASHBOARD_VERSION }.tar.gz \

WORKDIR /data

# bower requires this configuration parameter to allow bower install using root.
RUN echo '{ "allow_root": true }'>.bowerrc

# node-sass doesn't support Alpine, so we need the build toolchain.
RUN apk --update add ca-certificates git python build-base &&\
    npm install && npm run install &&\
    apk del ca-certificates git python build-base &&\
    rm -rf /var/cache/apk/*

EXPOSE 8080

CMD npm run start
