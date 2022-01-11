# TP Kubernetes
# RBAC
## Liens
- https://kubernetes.io/docs/reference/access-authn-authz/rbac/#kubectl-create-role
- https://kubernetes.io/docs/reference/access-authn-authz/service-accounts-admin/
- https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/
- https://devopscube.com/create-kubernetes-role/

## Context
- `kubectl config set-context dev --namespace=default --cluster=minikube --user=dev`
- `kubectl config set-context client --namespace=default --cluster=minikube --user=client`
## Users
```
users:
- name: client
  user:
    token: XXXXX
- name: dev
  user:
    token: XXXXX
```
