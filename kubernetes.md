## Kubernetes Commands

##Set context and namespace  

`kubectl config set current-context docker-desktop && kubectl config set-context --current --namespace=videoshare`

##Unset users, contexts, clusters  

```
kubectl config unset users.gke_project_zone_name

kubectl config unset contexts.aws_cluster1-kubernetes

kubectl config unset clusters.foobar-baz
```

Set default namespace
```
kubectl config set-context --current --namespace=my-namespace
```

Show current namespace
```
kubectl config view --minify -o jsonpath='{..namespace}'
```

## Kubernetes Basic Deployment

### Create Ingress Controller

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml`

**Via Helm (I prefer kubectl for the basic stuff, it keeps things simple :-))**
helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace

### Create deployment

The below command creates a deployment called timekeeper in the timekeeper namespace; the namespace should be created already. Please use a valid image either built locally or in a container registry 

`kubectl create deployment timekeeper --image=timekeeper:0.0.1 --port=8000 --namespace timekeeper`

### Create Service

The below command creates a service in the timekeeper namespace for the timekeeper deployment from the previous step

`kubectl expose deployment timekeeper --namespace timekeeper`


### Create Ingress rule 

The below command creates an ingress rule in the timekeeper namespace which will expose the timekeeper deployment/service via ingress-rule (This assumes that your ingress controller has already been created)

`kubectl create ingress timekeeper-localhost --class=nginx --rule="demo.localdev.me/*=timekeeper:8000" --namespace timekeeper`

### Update deployment image

The below command updates the timekeeper deployment from the first section from tag 0.0.1 to 0.0.2

`kubectl set image deployment/timekeeper timekeeper=timekeeper:0.0.2 --namespace timekeeper`

### Logs

Get pod and sidecar logs

```
kubectl logs order-service-749559957b-z9gkc -c wait-for-rabbitmq
```

Decode default (any) service account token

```
jq -R 'split(".") | select(length > 0) | .[0],.[1] | @base64d | fromjson' <<< $(kubectl exec -it eshop-apigwws-7ffbb9578d-h65vg -- cat /var/run/secrets/kubernetes.io/serviceaccount/token)
```

### Show what's stuck in terminating namespace

```
kubectl api-resources --verbs=list --namespaced -o name \
  | xargs -n 1 kubectl get --show-kind --ignore-not-found -n <namespace>
```
