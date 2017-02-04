# Run

$ kubectl create -f web.yaml
$ kubectl get pods -w -l app=nginx
$ kubectl get service nginx
$ kubectl get statefulset web
$ kubectl replace -f web.yaml
$ for i in 0 1 2 3; do kubectl exec web-$i -- sh -c 'hostname'; done
$ kubectl run -i --tty --image busybox dns-test --restart=Never --rm /bin/sh
  # nslookup web-0.nginx
  # nslookup web-2.nginx
$ kubectl delete pod -l app=nginx
$ kubectl get pods -w -l app=nginx

$ for i in 0 1; do kubectl exec web-$i -- sh -c 'hostname'; done
$ kubectl run -i --tty --image busybox dns-test --restart=Never --rm /bin/sh 
  # nslookup web-0.nginx
  # nslookup web-2.nginx
$ kubectl get pvc -l app=nginx
$ for i in 0 1; do kubectl exec web-$i -- sh -c 'echo $(hostname)xD > /usr/share/nginx/html/index.html'; done
$ for i in 0 1; do kubectl exec -it web-$i -- curl localhost; done
$ for i in 0 1; do kubectl exec web-$i -- chmod 755 /usr/share/nginx/html; done
$ for i in 0 1; do kubectl exec -it web-$i -- curl localhost; done

# Delete
$ kubectl delete pod -l app=nginx
$ for i in 0 1; do kubectl exec -it web-$i -- wget -O - localhost; done

# Scaling
$ kubectl get pods -w -l app=nginx
$ kubectl scale statefulset web --replicas=5

# Scaling down
$ kubectl get pods -w -l app=nginx
$ kubectl patch statefulset web -p '{"spec":{"replicas":3}}'

# Ordered Pod Termination
$ kubectl get pvc -l app=nginx

# Updating containers
$ kubectl patch statefulset web --type='json' -p='[{"op": "replace", "path": "/spec/template/spec/containers/0/image", "value":"gcr.io/google_containers/nginx-slim:0.7"}]'
$ kubectl delete pod web-0
$ for p in 0 1 2; do kubectl get po web-$p --template '{{range $i, $c := .spec.containers}}{{$c.image}}{{end}}'; echo; done
$ kubectl delete pod web-1 web-2

# Deleting StatefulSets
$ kubectl get pods -w -l app=nginx
$ kubectl delete statefulset web --cascade=false
$ kubectl delete pod web-0
$ kubectl create -f web.yaml 
$ for i in 0 1; do kubectl exec -it web-$i -- curl localhost; done

# Cascading Delete
$ kubectl delete statefulset web
$ kubectl delete service nginx

$ kubectl create -f web.yaml 
$ for i in 0 1; do kubectl exec -it web-$i -- curl localhost; done

$ kubectl delete service nginx
$ kubectl delete statefulset web






