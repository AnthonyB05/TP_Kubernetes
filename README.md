# TP Kubernetes
# NAMESPACE

## Créer un namespace via json
- `kubectl create -f nom-namespace.json`

## Assigner quota au namespace (le quota se trouve dans resource) :
- `kubectl apply -f quota-mem-cpu-demo.yaml -n=nom-namespace`

## Vérifier que le quota a bien été assigné :
- `kubectl get resourcequota -n nom-namespace`

⚠️ Ne pas mettre de quotas sur le namespace "monotoring" ⚠️

# INGRESS/NGINX

## Configuration
  configuration avec HELM:

- `helm repo add stable https://charts.helm.sh/stable`
- `helm install ingress -f config/helm-ingress-nginx.yml stable/nginx-ingress`

## Hosts

* sous linux/osx : /etc/hosts
* sous window: C:\Windows\System32\drivers\etc\hosts

 Ajouter :
  - 127.0.0.1 hello-world.ajs
  - 127.0.0.1 devops.ajs

## Validation des fichiers

- `kubectl apply -f "deployment && service"/hello-deployment.yml`
- `kubectl apply -f "deployment && service"/hello-service.yml`

- `kubectl apply -f "deployment && service"/devops-deployment.yml`
- `kubectl apply -f "deployment && service"/devops-service.yml`

- `kubectl create -f nginx/nginx.yml`


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
# MONITORING

## Installation

- `installer helm`
- `helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
- `helm repo update`
- `helm install prometheus prometheus-community/kube-prometheus-stack --namespace monotoring`

## Lancer

- `kubectl get pods -n monotoring`
- `kubectl port-forward -n monotoring prometheus-prometheus-prometheus-oper-prometheus-0 9090`
Via localhost:9090 vous pouvez voir Prometheus dashboard

- `kubectl port-forward -n monotoring prometheus-grafana-5c5885d488-b9mlj 3000`
Via localhost:3000 vous pouvez accèder à Grafana

## Se connecter à Grafana

login : admin
mdp : prom-operator

