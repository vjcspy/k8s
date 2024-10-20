# k8s-dashboard



## Install

```bash
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/
helm repo update
helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard \
--create-namespace --namespace kubernetes-dashboard \
```

## Config

Sử dụng cert được generated from cloudflare(10 năm)

```bash
# ví dụ tạo tls secret cho k8s-dashboard
kubectl create secret tls kubernetes-dashboard-tls --key common.key --cert common.crt -n kubernetes-dashboard
```



## Tạo ingress 

```bash
# apply file ingress
k apply -f ingress.yaml
```



## Access dashboard

```
# create ServiceAccount
kubectl create serviceaccount dashboard-admin -n kubernetes-dashboard

```

Sau khi tạo **Service Account**, bạn cần gán quyền **cluster-admin** cho nó bằng cách tạo một **ClusterRoleBinding**:

```bash
kubectl create clusterrolebinding dashboard-admin-binding \
  --clusterrole=cluster-admin \
  --serviceaccount=kubernetes-dashboard:dashboard-admin

```

Lấy secret

```bash
kubectl -n kubernetes-dashboard create token dashboard-admin
```

