##Set context and namespace  

`kubectl config set current-context docker-desktop && kubectl config set-context --current --namespace=videoshare`

##Unset users, contexts, clusters  

```
kubectl config unset users.gke_project_zone_name

kubectl config unset contexts.aws_cluster1-kubernetes

kubectl config unset clusters.foobar-baz
