# This dockerfile uses extends image https://hub.docker.com/sinlov/go-micro-cli
# VERSION 1
# Author: sinlov
# dockerfile offical document https://docs.docker.com/engine/reference/builder/
# https://hub.docker.com/_/node?tab=tags&page=1&ordering=last_updated&name=15.12.0-alpine
FROM node:15.12.0-alpine3.10

# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

RUN apk add --no-cache -U \
  make \
  libtool \
  libc-dev \
  gcc \
  g++ \
  python3 && \
  npm install --global libp2p-webrtc-star@0.21.2

# RUN npm install --global --registry=https://registry.npm.taobao.org libp2p-webrtc-star@0.21.2

WORKDIR /usr/src/myapp

EXPOSE 9090
ENV STAR_SIGNAL_HOST=0.0.0.0

CMD star-signal --host=$STAR_SIGNAL_HOST
# CMD ["tail",  "-f", "/etc/alpine-release"]
#ENTRYPOINT [ "go", "env" ]