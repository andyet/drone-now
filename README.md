# Drone-now

![Now logo](now.png?raw=true "now.sh")

[![Docker Pulls](https://img.shields.io/docker/pulls/lucap/drone-now.svg)](https://hub.docker.com/r/lucap/drone-now/)
[![](https://images.microbadger.com/badges/image/lucap/drone-now.svg)](https://microbadger.com/images/lucap/drone-now "Get your own image badge on microbadger.com")
[![GitHub release](https://img.shields.io/github/release/lucaperret/drone-now.svg)](https://github.com/lucaperret/drone-now/releases/latest)

Deploying to [now.sh](https://zeit.co/now) with [Drone](https://drone.io) CI. For the usage information and a listing of the available options please take a look at [the docs](DOCS.md).

## Usage

There are two ways to deploy.

### From docker

Deploy the working directory to now.

```bash
docker run --rm \
  -e NOW_TOKEN=xxxxxxx \
  -e PLUGIN_DEPLOY_NAME=my-deployment-name \
  -e PLUGIN_ALIAS=my-deployment-alias.now.sh \
  -v $(pwd):$(pwd) \
  -w $(pwd) \
  lucap/drone-now
```

### From Drone CI

```yaml
pipeline:
  now:
    image: lucap/drone-now
    deploy_name: my-deployment-name
    type: static
    team: xxxxxxxx
    directory: public
    alias: my.deployment.com
    secrets: [ now_token ]
```
