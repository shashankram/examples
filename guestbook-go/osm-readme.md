```bash
osm install

kubectl create ns guestbook
osm namespace add guestbook

cd guestbook-go
kubectl create -f redis-primary-controller.json -n guestbook
kubectl create -f redis-primary-service.json -n guestbook
kubectl create -f redis-secondary-controller.json -n guestbook
kubectl create -f redis-secondary-service.json -n guestbook
kubectl create -f guestbook-controller.json -n guestbook
kubectl create -f guestbook-service.json -n guestbook

kubectl port-forward <guestbook-pod> -n guestbook 3000:3000

kubectl apply -f smi-policies.yaml
```
