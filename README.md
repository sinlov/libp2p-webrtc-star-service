# libp2p-webrtc-star-service

[![docker build](https://img.shields.io/docker/cloud/build/sinlov/libp2p-webrtc-star-service)](https://hub.docker.com/r/sinlov/libp2p-webrtc-star-service)
[![docker version semver](https://img.shields.io/docker/v/sinlov/libp2p-webrtc-star-service?sort=semver)](https://hub.docker.com/r/sinlov/libp2p-webrtc-star-service/tags?page=1&ordering=last_updated)
[![docker image size](https://img.shields.io/docker/image-size/sinlov/libp2p-webrtc-star-service)](https://hub.docker.com/r/sinlov/libp2p-webrtc-star-service)

- docker hub see https://hub.docker.com/r/sinlov/libp2p-webrtc-star-service
- this is fast way to run https://www.npmjs.com/package/libp2p-webrtc-star

## libp2p-webrtc-star

- source https://github.com/libp2p/js-libp2p-webrtc-star
- document https://www.npmjs.com/package/libp2p-webrtc-star [![NPM Version](http://img.shields.io/npm/v/libp2p-webrtc-star.svg?style=flat)](https://www.npmjs.org/package/libp2p-webrtc-star)

## fast use

```sh
docker run --rm \
  --name star-signal \
  -p 9090:9090 \
  sinlov/libp2p-webrtc-star-service:latest
```

## docker-compose

```yml
# copy right
# Licenses http://www.apache.org/licenses/LICENSE-2.0
# more info see https://docs.docker.com/compose/compose-file/ or https://docker.github.io/compose/compose-file/
version: '3.7'
networks:
  default:
services:
  star-signal:
    container_name: 'star-signal'
    image: sinlov/libp2p-webrtc-star-service:0.21.2-alpine # https://hub.docker.com/r/sinlov/libp2p-webrtc-star-service/tags?page=1&ordering=last_updated
    ports:
      - '9090:9090'
    environment:
      - STAR_SIGNAL_HOST=0.0.0.0
    restart: always # on-failure:3 or unless-stopped always default no
```