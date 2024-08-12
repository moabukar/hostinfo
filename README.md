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

To curl a k8s service backed by hostinfo instances:

```bash
$ kubectl run test-hi --image moabukar/hostinfo:57e740e --port 9898

$ kubectl expose pod test-hi --port 80 --target-port 9898
```

Now from another pod:

```bash
$ kubectl run -it --rm netshoot --image nicolaka/netshoot

$ curl test-hi.default.svc.cluster.local

test-hi 10.2.1.154
```

