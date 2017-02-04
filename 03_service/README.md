Instructions:

# Run
$ kubectl run hello-world --replicas=3 --labels="run=load-balancer-example" --image=hello-node:v2 --port=8080
$ kubectl get deployments hello-world
$ kubectl describe deployments hello-world
$ kubectl get replicasets
$ kubectl describe replicasets

# Creating service
$ kubectl expose deployment hello-world --type=NodePort --name=example-service
$ kubectl describe services example-service
$ kubectl get pods --selector="run=load-balancer-example" --output=wide
$ minikube service example-service

# Terminating
$ kubectl delete services example-service
$ kubectl delete deployment hello-world
