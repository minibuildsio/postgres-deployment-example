# Deploy Postgres to Kubernetes

This repo demos deploying Postgres to Kubernetes check out the associated article: https://minibuilds.io/posts/kubernetes-postgres-deployment/.

## Order of commands

```
kubectl apply -f db-namespace.yaml
```

```
kubectl apply -f db-pv.yaml
kubectl apply -f db-pvc.yaml
```

```
kubectl apply -f db-pg-cm.yaml
kubectl create secret generic db-pg-secret -n db --from-literal=password='replace_with_real_password'
kubectl apply -f db-pg-deployment.yaml
kubectl apply -f db-pg-svc.yaml
```

```
kubectl apply -f db-pgadmin-cm.yaml
kubectl create secret generic db-pgadmin-secret -n db --from-literal=password='replace_with_real_password'
kubectl apply -f db-pgadmin-deployment.yaml
kubectl apply -f db-pgadmin-svc.yaml   
```

```
minikube service -n db --url db-pgadmin-svc
```