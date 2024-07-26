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

charts
* deployment
* service
* secret
```shell
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f secret.yaml
# heml

```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4OTI4NTkzNDksLTk5ODI0MTgzMl19
-->