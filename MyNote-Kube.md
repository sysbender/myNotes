# MyNote-Kube

## MyNote-Kube

### components

* deployment - app
  * replicaset
    * Pod

#### yaml - define resource

```
kubectl create -f my.yaml
kubectl delete -f my.yaml

kubectl get <resources> -o yaml > myresource.yaml

```

#### api

* kubectl
  * api-versions
  * api-resources
  * explain pod.spec.containers

#### pod management

not using naked pod

```
kubectl create -f mypod.yaml


```

* describe pods
* get pods
* get pods -o yaml
* delete pods mypod

## helm

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

### setup

```shell

choco install kubernetes-helm
# reinstall minikube
minikube delete && minikube start --memory 4096


```

### example

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install mysql bitnami/mysql

kubectl get pods --all-namespaces
helm list
helm uninstall mysql 
```

stateful sets - give pod garantee name, rather than

### example - prom

````
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
````

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

### chart value

to customize

```sh
helm show values prom/kube-prometheus-stack
# update a value by set
helm upgrade monitoring prom/kube-prometheus-stack --set grafana.adminPassword=admi

# which value name : https://github.com/grafana/helm-charts/tree/main/charts/grafana
helm upgrade monitoring prom/kube-prometheus-stack --values=values

```



````yaml
```yaml
## Using default values from https://github.com/grafana/helm-charts/blob/main/charts/grafana/values.yaml
##
grafana:

  adminPassword: admin
 
  ## Passed to grafana subchart and used by servicemonitor below
  ##
  service:
    portName: http-web
    ipFamilies: []
    ipFamilyPolicy: ""
    type: NodePort
    nodePort: 30008
```
````



* snowflake server/cluster - every snowflake is different
* phenix server/cluster - replicable&#x20;

don't use helm install

#### pull and install

```
# helm pull
helm pull bitnami/mysql --untar=true
helm pull prom/kube-prometheus-stack --untar=true


helm install monitoring ./kube-prometheus-stack/

helm upgrade monitoring --values=myvalues.yaml .

# using generated template and apply by kubectl
helm template monitoring ./kube-prometheus-stack/ --values=./kube-prometheus-stack/myvalues.yaml > monitoring.yaml

kubectl apply -f monitoring.yaml



```



```
https://github.com/DickChesterwood/k8s-fleetman/blob/master/_course_files/Intel_AMD_Edition/Going%20Further%20with%20Kubernetes/Helm/fleetman-helm-demo-start.yaml
```



