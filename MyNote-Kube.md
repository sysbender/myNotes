# MyNote-Kube


## components

* deployment - app
    * replicaset
        * Pod



### yaml - define resource

```
kubectl create -f my.yaml
kubectl delete -f my.yaml

kubectl get <resources> -o yaml > myresource.yaml

```


### api

* kubectl 
    * api-versions
    * api-resources
    * explain pod.spec.containers


 ### pod management
 
 not using naked pod
 ```
 kubectl create -f mypod.yaml
 
 
 ```
 * describe pods
 * get pods
 * get pods <podname> -o yaml
 *  delete pods mypod


# helm
a Helm chart is a collection of files that describe the necessary **resources**, **dependencies**, and **configuration options** for an application.

Helm charts package all the required Kubernetes resources, such as deployments, services, and configmaps, into a single package.
* package
* template
* dependency

charts
* deployment
* service
* secret
```shell
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f secret.yaml
# helm
helm install -name mychart ./mychart

```
artifacthub.io



```
helm repo add bitnami 
```
## setup

```shell

choco install kubernetes-helm
# reinstall minikube
minikube delete && minikube start --memory 4096


```
## example
```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install mysql bitnami/mysql

kubectl get pods --all-namespaces
helm list
helm uninstall mysql 
```
stateful sets - give pod garantee name, rather than 

 ## prom
 ```
```bash
helm repo add prom https://prometheus-community.github.io/helm-charts
```
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYwNzU3ODA3NSwxMTc3MTUwNzY3LDExOT
MxMzc0NTUsLTE5NTUyMzU3Nyw4ODgwNDE2ODIsNzQ2MTM3MzM1
LC04NTM5MzY3OTEsLTM3NDE4NzQ1MiwxNDY4NTI5MzExLC0xMT
Q3NDM2OTM0LC01OTM1NTM0MjEsLTk5ODI0MTgzMl19
-->