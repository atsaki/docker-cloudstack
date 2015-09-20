# CloudStack Simulator Docker Image

Docker Image that contains CloudStack simualtor

## Usage

Just run the contanier

```sh
$ docker run --name cloudstack -d -p 8080:8080 atsaki/cloudstack-simulator
```

There are some tags to use pre-configured images.

```sh
$ docker run --name cloudstack -d -p 8080:8080 atsaki/cloudstack-simulator:4.5.2-basic
$ docker run --name cloudstack -d -p 8080:8080 atsaki/cloudstack-simulator:4.5.2-advanced
```

## Acknowledgement

The Dockerfile is based on [cloudstack/simulator](https://hub.docker.com/r/cloudstack/simulator/).

