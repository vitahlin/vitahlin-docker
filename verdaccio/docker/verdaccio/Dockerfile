FROM node:alpine

RUN apk --no-cache add wget openssl && \
    wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64 && \
    chmod +x /usr/local/bin/dumb-init && \
    apk del openssl && \
    apk --no-cache add ca-certificates wget && \
    apk --no-cache add g++ gcc libgcc libstdc++ linux-headers make python && \
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://raw.githubusercontent.com/sgerrand/alpine-pkg-glibc/master/sgerrand.rsa.pub && \
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.25-r0/glibc-2.25-r0.apk && \
    apk add glibc-2.25-r0.apk

ENV APPDIR /usr/local/app

WORKDIR $APPDIR

ADD . $APPDIR

USER root

RUN npm install yarn -g
RUN yarn global add verdaccio

RUN mkdir -p /verdaccio/storage /verdaccio/plugins /verdaccio/conf

ADD ./conf/config.yaml /verdaccio/conf/config.yaml

RUN addgroup -S verdaccio && adduser -S -G verdaccio verdaccio && \
    chown -R verdaccio:verdaccio "$APPDIR" && \
    chown -R verdaccio:verdaccio /verdaccio

USER verdaccio

ENV PORT 4873

EXPOSE $PORT

VOLUME ["/verdaccio"]

CMD verdaccio --config /verdaccio/conf/config.yaml --listen http://0.0.0.0:${PORT}