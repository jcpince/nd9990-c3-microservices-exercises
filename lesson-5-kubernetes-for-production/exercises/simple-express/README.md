# Overview
This is a very simple, bare-bones NodeJS and ExpressJS project created for you to use with Docker.

# Local Setup
* Install dependencies: `npm install`
* Run server: `node server.js`

# Usage
By default, the application should be loaded on `localhost:8080`. It should provide an HTTP 200 response when loaded at `localhost:8080/health`.

# Container Setup
* Build image: `docker build .`
* Run container with image: `docker run {image_id}` where `image_id` can be retrieved by running `docker images` and found under the column `IMAGE ID`

# Container teardown
* Remove container: `docker kill {container_id}` where `container_id` can be retrieved by running `docker ps` and found under the column `CONTAINER ID`

# Upload on docker hub
docker build -t jcpince/simple-express:latest .
docker push jcpince/simple-express:latest

# Test
kubectl apply -f deploy/deployment.yaml
kubectl apply -f deploy/service.yaml

kubectl get pods
kubectl exec -it <my-app-2-xxx> bash
curl http://my-app-2-svc:8080/health
> Returns hello
