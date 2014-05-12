## Redis Dockerfile


This repository contains **Dockerfile** of [Redis](http://redis.io/) used in Ask.fm.

### Dependencies

* [dockerfile/ubuntu](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.io/).
2. Run **docker build github.com/pinkokio/redis**


### Usage

#### Run `redis-server`

    docker run -d --name redis -p 6379:6379 dockerfile/redis

#### Run `redis-server` with persistent data directory. (creates `dump.rdb`)

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis dockerfile/redis

#### Run `redis-server` with persistent data directory and password.

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis dockerfile/redis redis-server /etc/redis/redis.conf --requirepass <password>

#### Run `redis-cli`

    docker run -it --rm --link redis:redis dockerfile/redis bash -c 'redis-cli -h $REDIS_PORT_6379_TCP_ADDR'
