# K8S

## Install nginx-ingress

```bash
helm install nginx-ingress oci://ghcr.io/nginxinc/charts/nginx-ingress --version 1.4.0
```


## Node conig

### Tạo tls secret

```bash
# ví dụ tạo tls secret cho k8s-dashboard
kubectl create secret tls kubernetes-dashboard-tls --key common.key --cert common.crt -n kubernetes-dashboard
```

