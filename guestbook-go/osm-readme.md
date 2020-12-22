```bash
bin/osm install --osm-image-tag=bf1f2b28f790adfa6cb8d49690aa61e1b40d6b57

kubectl create ns guestbook
osm namespace add guestbook

cd guestbook-go
kubectl create -f redis-master-controller.json -n guestbook
kubectl create -f redis-master-service.json -n guestbook
kubectl create -f redis-slave-controller.json -n guestbook
kubectl create -f redis-slave-service.json -n guestbook
kubectl create -f guestbook-controller.json -n guestbook
kubectl create -f guestbook-service.json -n guestbook

kubectl port-forward <guestbook-pod> -n guestbook 3000:3000

kubectl apply -f smi-policies.yaml
```