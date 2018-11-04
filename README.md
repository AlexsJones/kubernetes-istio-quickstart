# kubernetes-istio-quickstart



## Dependencies
- go get github.com/AlexsJones/vortex
- Admin binding e.g.
```
kubectl create clusterrolebinding cluster-admin-binding \
    --clusterrole=cluster-admin \
    --user=$(gcloud config get-value core/account)
```

## setup
- Get Istio and install it on the path https://istio.io/docs/setup/kubernetes/download-release/
- Install istio, kubectl create -f <ISTIO_PATH>/install/kubernetes/istio-demo-auth.yaml
- kubectl label namespace default istio-injection=enabled
- ./build_environment.sh default
- kubectl create -f deployment


## Access

```
kubectl get svc/istio-ingressgateway --namespace=istio-system
```

Use the external IP to access the istio gateway and route to the correct virtual service


## JaegerUI

```
kubectl port-forward -n istio-system $(kubectl get pod -n istio-system -l app=jaeger -o jsonpath='{.items[0].metadata.name}') 16686:16686 &
```
