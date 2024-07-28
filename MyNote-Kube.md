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

 ## example - prom
 ```
```bash
helm repo add prom https://prometheus-community.github.io/helm-charts
helm repo list
helm repo update

```bash
helm install monitoring prom/kube-prometheus-stack
helm list
kubectl --namespace default get pods -l "release=monitoring"

kubectl edit svc monitoring-grafana
minikube ip  # find ip of minikube node
```

```
  - name: http-web
    port: 80
    protocol: TCP
    targetPort: 3000
    nodePort: 30001  # new
  selector:
    app.kubernetes.io/instance: monitoring
    app.kubernetes.io/name: grafana
  sessionAffinity: None
  type: NodePort  # change from ClusterPort
```

## chart value
to customize


`helm show values prom/kube-prometheus-stack`

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODA5MjU4NzcsMTc5MTYwODQ3NiwyNj
UyNDgzOTYsNzU4NDQ2MzU1LC03MTAxOTI2NTIsLTIyMjgxMjgy
MSwxMTc3MTUwNzY3LDExOTMxMzc0NTUsLTE5NTUyMzU3Nyw4OD
gwNDE2ODIsNzQ2MTM3MzM1LC04NTM5MzY3OTEsLTM3NDE4NzQ1
MiwxNDY4NTI5MzExLC0xMTQ3NDM2OTM0LC01OTM1NTM0MjEsLT
k5ODI0MTgzMl19
-->