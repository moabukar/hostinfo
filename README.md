# hostinfo

Simple Go microservice which returns a host info string. Accessible via curl, wget, etc. Listens on port 9898 by default, if an `int` is passed on the command line, that port is used instead. Particularly useful when demonstrating K8s service routing mesh operation (deploy several replicas of these, create a service for them then curl the service sequentially to see various hosts engaged).
