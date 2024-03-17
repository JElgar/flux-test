Testing of flux

## Local Dev

```
export GITHUB_TOKEN=
minikube start --cpus 6 --memory 8192
minikube addons enable ingress
minikube addons enable metrics-server
flux bootstrap github --owner=jelgar --repository=flux-test --path=clusters/nowu
```

## Prometheus

```
kubectl port-forward -n monitoring deployments/prometheus-grafana 3000
```
username: admin
password: prom-operator

## Weave Gitops

```
kubectl port-forward --namespace flux-system svc/ww-gitops-weave-gitops 9001:9001
```

TODO: Change this password

username: admin
password: admin

## Enable ssl locally

Generate a root certificate
