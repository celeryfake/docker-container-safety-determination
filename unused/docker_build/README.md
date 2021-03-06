# How to build docker image and push to private-registry


## Docker build  
see [this link](https://yeasy.gitbooks.io/docker_practice/content/image/dockerfile/copy.html)  
use **COPY** to copy files to the new image.  
see the reference link for **RUN** and **CMD** command.  

build command:  
```shell
$ docker build -t mian:v1 docker_build_dir
```

## Docker push  
### enable push to insecure registry  
Add configurate file to the client host to connect to insecure private registry.  
```shell
$ sudo vim /etc/docker/daemon.json
```
add below to the configuration file  
```python
{
"insecure-registries": ["ip:port"]
}
```
restart docker daemon  
```shell
$ sudo service docker stop
$ dockerd &
```

[reference link](https://github.com/docker/distribution/issues/1874)
### push to registry
```shell
$ docker tag image_name:tag 159.65.238.188:5001/dir_name
$ docker push 159.65.238.188:5001/dir_name
```

## Docker save image to local file system
```shell
$ docker save -o a.tar mian:v2
```
