```bash
osm install --osm-image-tag=b7337ab144d0126fa44312bc3001f563183ffb76

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