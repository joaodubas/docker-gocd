# Go Continuous Delivery and Release Management

These are the docker images for server/agent [Go Continuous Delivery and
Release Management][gocd].

## Installation

To install go server and agent:

```bash
$ docker pull joaodubas/gocd-server:latest
$ docker pull joaodubas/gocd-agent:latest
```

## Building

To build go server and agent:

```bash
$ docker build --rm --tag $(cat base/REPOSITORY):latest base
$ docker build --rm --tag $(cat server/REPOSITORY):latest server
$ docker build --rm --tag $(cat agent/REPOSITORY):latest agent
```

The `base` image contains common layers between server and agent, such as,
system dependencies, environment variables among others.

## Running

To run the images:

```bash
$ docker run -d --name gocd-server --hostname gocd-server joaodubas/gocd-server:latest
$ docker run -d --name gocd-agent-01 --hostname gocd-agent-01 --link gocd-server:server --env GO_SERVER=server joaodubas/gocd-agent:latest
```

[gocd]: http://www.go.cd
