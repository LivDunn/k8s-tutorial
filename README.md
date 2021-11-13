# k8s-tutorial
Small node app to use for k8s tutorial 


build container 

docker build -t k8s-tutorial .
docker tag k8s-tutorial {YOUR_HUB_NAME}/k8s-tutorial:version1
docker push {YOUR_HUB_NAME}/k8s-tutorial:version1

-- Might have issue pushing from the cmd line - if so login via your docker desktop app and push from there 

download minikub

use binary as brew gives an old version with a bug in the proxy 

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube


minikube start

minikube status

run this kubectl get po -A and wait until all services show 1/1

minikube dashboard -- this might hang on checking proxy give it time it finally kicks in

-- imperitive commands 

kubectl create deployment k8s-demo --image=oliviajdunnett/k8s-tutorial:version1

kubectl get deployments

kubectl get pods

kubectl delete deployments k8s-demo

kubectl expose deployment k8s-demo --type=LoadBalancer --port=8080

minikube service k8s-demo

Declaritively 

kubectl apply -f=deployment.yaml 

kubectl apply -f=service.yaml 