# k8s-tutorial
Small node app to use for k8s tutorial 

# Tools & set up required

## download kubectl

`brew install kubectl`

## download docker

Docker - https://docs.docker.com/desktop/mac/install/

## download minikube

use binary as brew gives an old version with a bug in the proxy 

`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64`

`sudo install minikube-darwin-amd64 /usr/local/bin/minikube`


`minikube start`

`minikube status`

run this `kubectl get po -A` and wait until all services show 1/1

`minikube dashboard` -- this might hang on checking proxy give it time it finally kicks in


# build container 

`docker build -t k8s-tutorial .`

`docker tag k8s-tutorial {YOUR_HUB_NAME}/k8s-tutorial:latest`

`docker push {YOUR_HUB_NAME}/k8s-tutorial:latest`

-- Might have issue pushing from the cmd line - if so login via your docker desktop app and push from there 


# imperative commands 

`kubectl create deployment k8s-demo --image=oliviajdunnett/k8s-tutorial:latest`

`kubectl get deployments`

`kubectl get pods`

`kubectl expose deployment k8s-demo --type=LoadBalancer --port=8080`

`minikube service k8s-demo`

`kubectl scale deployment/k8s-demo --replicas=3`

clean up
`kubectl delete deployments k8s-demo` 
`kubectl delete services k8s-demo`


# Declaratively

`kubectl apply -f=deployment.yaml `

`kubectl apply -f=service.yaml `
`minikube service k8s-tutorial-service`

clean up 
`kubectl delete -f=deployment.yaml`
`kubectl delete -f=service.yaml`