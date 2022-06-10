# myNote-docker


```
docker search

docker run -it busybox /bin/sh

ctrl-Z bg # put into background

docker run -d nginx

exit

# ctrl-p + ctrl-q  : quit the connection
docker ps --all


docker create
docker start
docker stop #SIGTERM
docker kill 
docker rm

docker inspect
docker logs
docker stats

 ps fax | grep docker -A 3

```

## daily management


```
 # search
 docker search --filter "is-official=true" ubuntu
 
 docker pull centos:centos6
 
 docker images
 
 
 
```


## docker image

### create docker image 
* docker file - From,Add/Copy,  Run , Entrypoint/CMD
* dock commit  - docker commit/save/load

### docker private registry
* run docker-distribution daemon on centos
* run registry container
```
docker run -d -p 5000:5000 --restart=always --name registry registry:latest

docker pull fedora
docker images

docker tag fedora:latest localhost:5000/myfedora  # tag is required before push

docker push localhost:5000/myfedora

docker rmi fedora
docker pull localhost:5000/myfedora



```

### storage
* cow - copy on write, layer
* bind mount  - mount source=/host target=/container
* volume mount - 


### networking
* bridge -default
* host
* overlay
* macvlan
* none
* plugins


## docker command graph/diagram

http://docker-saigon.github.io/post/Docker-Internals/
![](https://i.imgur.com/ne3q1IZ.png)



https://yuehhua.github.io/2018/07/21/04-reference/

![](https://i.imgur.com/b5vLFsA.png)



![](https://i.imgur.com/dn818cs.png)


https://github.com/Haufe-Lexware/docker-style-guide/blob/master/DockerImage.md


![](https://i.imgur.com/4VvF51l.png)
