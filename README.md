Testing of flux

## Local Dev

```
export GITHUB_TOKEN=
minikube start --cpus 6 --memory 8192
minikube addons enable ingress
minikube addons enable metrics-server
kubectl get crd gateways.gateway.networking.k8s.io &> /dev/null || \
  { kubectl kustomize "github.com/kubernetes-sigs/gateway-api/config/crd?ref=444631bfe06f3bcca5d0eadf1857eac1d369421d" | kubectl apply -f -; }
flux bootstrap github --owner=jelgar --repository=flux-test --path=clusters/nowu
```

```
kubectl apply -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.0.0/standard-install.yaml
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

## Kiali

kubectl -n istio-system create token kiali-service-account

## Enable ssl locally

Generate a root certificate

## Notes

https://istio.io/latest/docs/setup/additional-setup/getting-started/
