# k8s-dashboard



## Install

```bash
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/
helm repo update
helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard \
--create-namespace --namespace kubernetes-dashboard \
```

## Using

Sử dụng cert được generated from cloudflare(10 năm)

```bash
# ví dụ tạo tls secret cho k8s-dashboard
kubectl create secret tls kubernetes-dashboard-tls --key common.key --cert common.crt -n kubernetes-dashboard
```

Sau đó apply toàn bộ thư mục dashboard để tạo ingress, service account(dùng để access)
```bash
k apply -f dashboard
```

### Access dashboard

```bash
kubectl get secret admin-user -n kubernetes-dashboard -o jsonpath={".data.token"} | base64 -d
```

