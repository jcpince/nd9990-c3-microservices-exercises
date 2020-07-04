# Overview
This is a very simple example of how to deploy a reverse-proxy from ngnix.

# Container Setup
* Build image: `docker build .`
* Run container with image: `docker run {image_id}` where `image_id` can be retrieved by running `docker images` and found under the column `IMAGE ID`

# Container teardown
* Remove container: `docker kill {container_id}` where `container_id` can be retrieved by running `docker ps` and found under the column `CONTAINER ID`

# Upload on docker hub
docker build -t jcpince/reverse-proxy:latest .
docker push jcpince/reverse-proxy:latest

# Test
kubectl apply -f deploy

kubectl get pods
kubectl exec -it <my-app-2-xxx> bash

* Check that the simple-express is still up and running(See simple-express project for details)
root@my-app-2-7d6fbfc5cf-k7xqk:/usr/src/app# curl http://my-app-2-svc:8080/health
> Returns Hello!

* Now, check that the proxy is ok
root@my-app-2-7d6fbfc5cf-k7xqk:/usr/src/app# curl http://reverse-proxy-svc:8080/api/health
> Returns Hello!

* Tear down the pods
kubectl delete -f deploy
