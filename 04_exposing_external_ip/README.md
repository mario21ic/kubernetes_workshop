# Run
$ kubectl run hello-world --replicas=5 --labels="run=load-balancer-example" --image=hello-node:v2 --port=8080
$ kubectl get deployments hello-world
$ kubectl describe deployments hello-world

$ kubectl get replicasets
$ kubectl describe replicasets

$ kubectl expose deployment hello-world --type=LoadBalancer --name=my-service
$ kubectl get services my-service

$ curl $(minikube service my-service --url)

$ kubectl delete service my-service
$ kubectl delete deployment hello-world
