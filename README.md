# hostinfo

Simple Go microservice which returns a host info string. Accessible via curl, wget, etc. Listens on port 9898 by default, if an `int` is passed on the command line, that port is used instead. Particularly useful when demonstrating K8s service routing mesh operation (deploy several replicas of these, create a service for them then curl the service sequentially to see various hosts engaged).

## Go

```bash

> go run hi.go 
2024/08/12 11:56:04 mo-local.lan 192.168.1.186 9898

```

## Docker

```bash

docker build -t hi .
docker run hi

> docker run hi
2024/08/12 10:57:01 b13b6e4bc087 172.17.0.2 9898

```

## K8s

```bash


```
