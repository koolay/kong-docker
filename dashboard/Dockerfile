FROM mhart/alpine-node
MAINTAINER koolay

ENV DASHBOARD_VERSION 1.1.2

RUN mkdir /data && cd /data

WORKDIR /data

# node-sass doesn't support Alpine, so we need the build toolchain.
RUN apk --update add ca-certificates git python build-base

RUN git clone https://github.com/PGBI/kong-dashboard.git ./ && rm -rf .git/

# bower requires this configuration parameter to allow bower install using root.
RUN echo '{ "allow_root": true }'>.bowerrc

RUN npm install && npm run install


# clean
RUN apk del ca-certificates git python build-base &&\
    rm -rf /var/cache/apk/*

EXPOSE 8080

CMD npm run start
