# Docker and K8s: Notes

* Docker Installation :[Docker desktop](https://www.docker.com/products/docker-desktop)
* Check Docker version
  * `$ docker --version`
* Pull Docker Image from Docker hub
  * `$ docker pull nginx` - pulls latest image
  * `$ docker pull nginx:[tag]` - pulls specific version of docker
* List all Docker images
  * `$ docker images`
  * `$ docker image ls`
* Run Docker container
  * `$ docker run nginx:[tag]` - Run container but terminal is handing
  * `$ docker run -d nginx:[tag]` - Run container in detached mode (-d stands for detached)
* List Running Container
  * `$ docker container ls`
  * `$ docker ps` - This is prefered way to list container.
* Stop Docker container by container name or container id
  * `$ docker stop [CONTAINER ID/NAMES]`
* **PORT** : Mapping port from host to container
  * `$ docker run -d -p 8080:80 nginx`
* **PORT** : Mapping multiple port from host to single container
  * `$ docker run -d -p 8080:80 -p 3000:80 nginx`
* Start a stopped container by name or Id
  * `$ docker start [CONTAINER ID/NAMES]`  
* Docker ps
  * `$ docker ps --help`
  * `$ docker ps -a` - List all running and stoped container
  * `$ docker ps -q` - List containerid of running and stoped container
* Remove or Delete container
  * `$ docker rm [containerid]` - only stoped container
  * `$ docker rm -f [containerid]` - forcfully remove running container
  * `$ docker rm ${docker ps -aq}` - Remove  all container.
* How to name container for simplicity with `--name`
  * `$ docker run --name mywebsite -d -p 8080:80 nginx`
### **VOLUME:**  
* **VOLUME:** (A)allow sharing data(files and folders) between host and container or between containers.
  * `$ docker run --name mywebsite -v $(pwd):/usr/share/nginx/html:ro -d -p 8080:80 nginx`
    * Share volume between host and container
    * -v is user for volume 
    * -v [host location]:[conatiner loation]:[read access]
    * `:ro` container can only read this file and cannot write to location.
* How to use docker container terminal
 * `$ docker exec -it [containeId/containername] bash`    
* **VOLUME:** (B)allow sharing data(files and folders) between between containers.
  * `$ docker run --name mywebsite-copy --volume-from mywebsite $(pwd):/usr/share/nginx/html:ro -d -p 8080:80 nginx`
    * Share volume between container
    * --volume-from specify volume from another container 
    
### **Dockerfile:** [Link](https://docs.docker.com/engine/reference/builder/)