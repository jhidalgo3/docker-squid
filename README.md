# Description

Run Squid proxy as a service for your Kubernetes containers

# Install Chart Helm

```
kubectl create ns proxy

helm upgrade --install squid -f values.yaml -n proxy ./squid-helm-chart
```

## Install from Chart Helm repository

```
helm repo add jhidalgo3 https://jhidalgo3.github.io/charts
helm repo update

helm upgrade --install squid -n proxy jhidalgo3/squid -f values.yaml
```

## Testing

Deploy curl-test pod

```
kubectl apply -f curl-test-pod

kubectl exec -ti curl-test -n proxy -- curl -v http://httpbin.org/headers
```

[Check proxy](http://amibehindaproxy.com/)


# Docs to conf a parent proxy

* [Configure Squid Proxy To Forward To A Parent Proxy](https://www.rootusers.com/configure-squid-proxy-to-forward-to-a-parent-proxy/)

# Thanks

[Original Helm Chart](https://github.com/honestica/lifen-charts/squid)
