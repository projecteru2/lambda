Lambda
=============
[![CircleCI](https://circleci.com/gh/projecteru2/lambda/tree/master.svg?style=shield)](https://circleci.com/gh/projecteru2/lambda/tree/master)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/a91da2853c4c4dc3b155f3397778f47e)](https://www.codacy.com/app/CMGS/lambda?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=projecteru2/lambda&amp;utm_campaign=Badge_Grade)

Run anything in container on Eru

NOTE: Image should have a user named lambda for running command, if there was no lambda user inside, please use raw mode.

We build a run-lambda image named [projecteru2/footstone:run-lambda](https://hub.docker.com/r/projecteru2/footstone/). This is the [Dockerfile](https://github.com/projecteru2/footstone/blob/master/run-lambda/Dockerfile).

### Params

Must

* config
* name
* command

Optional

* env
* volumes
* raw

Get from config (can override)

* pod
* network
* image
* cpu
* mem
* timeout
* stdin

Default

* count
* admin
* debug
* help
* version

### Admin mode

if admin is `True`

pod and volumes will be rewrited.

their values get from config file.

### Developing

#### Test

`make test`

#### Build

`make build`

#### RPM

`./make-rpm`

To make rpm, you should install [fpm](https://github.com/jordansissel/fpm) first.

### Dockerized Lambda

Image: [projecteru2/lambda](https://hub.docker.com/r/projecteru2/lambda/)

```shell
docker run -it --rm \
  --net host \
  --name eru-lambda \
  -v <HOST_CONFIG_DIR_PATH>:/etc/eru \
  projecteru2/lambda \
  /usr/bin/eru-lambda <PARAMS>
```
