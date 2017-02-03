# Deployment
$ kubectl create -f deployment.yaml

# Monitoring
$ kubectl get pods -l app=nginx

# Upgrade
$ kubectl apply -f deployment-update.yaml

# Monitoring
$ kubectl get pods -l app=nginx

# Scale
$ kubectl apply -f deployment-scale.yaml

# Monitoring
$ kubectl get pods -l app=nginx

# Deleting
$ kubectl delete deployment nginx-deployment
