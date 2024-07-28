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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODc5ODE0MjgsMjY1MjQ4Mzk2LDc1OD
Q0NjM1NSwtNzEwMTkyNjUyLC0yMjI4MTI4MjEsMTE3NzE1MDc2
NywxMTkzMTM3NDU1LC0xOTU1MjM1NzcsODg4MDQxNjgyLDc0Nj
EzNzMzNSwtODUzOTM2NzkxLC0zNzQxODc0NTIsMTQ2ODUyOTMx
MSwtMTE0NzQzNjkzNCwtNTkzNTUzNDIxLC05OTgyNDE4MzJdfQ
==
-->