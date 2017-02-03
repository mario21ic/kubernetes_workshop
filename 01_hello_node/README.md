Instructions:

# Start
$ minikube start  --memory=6000 --vm-driver=kvm 
$ eval $(minikube docker-env)

# Build
$ docker build -t hello-node:v1 .

# Monitoring
$ watch kubectl get pods 
$ watch kubectl get service
$ watch kubectl get deployment

# Run
$ kubectl run hello-node --image=hello-node:v1 --port=8080
$ kubectl expose deployment hello-node --type=LoadBalancer 
$ minikube service hello-node

# Modify file server.js
$ docker build -t hello-node:v2 .
$ kubectl set image deployment/hello-node hello-node=hello-node:v2
$ minikube service hello-node
