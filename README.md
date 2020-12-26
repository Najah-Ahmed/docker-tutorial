# Docker

![docker](Moby-logo.png)

---

## Docker Command

> Docker pull command

```

docker container run --publish 80:80 --detach --name  webserver nginx

docker container run -d -p 3306:3306 --name db -e MYSQL_RANDOM_ROOT_PASSWORD=yes mysql

```

> Docker Useful commands

```
   docker inspect

   docker stats
```

> list all running container

```
docker container ls
```

> list all container

```
docker container ls -a
```

> Docker for running os and get inside

```
docker container run -it --name ubuntu4 ubuntu
```

> Docker run Existing Local Image

```
docker container run -ai ubuntu
```

> Docker get inside container by bash

```
docker container run -it --name webngix nginx  bash
```

> Start container

```
docker container start  -ai  ubuntu
```

```
docker container exec -it mysql bash
```

---

# Docker network

```
docker network ls
docker network create my_network
docker container run -d -p 8000:80 --name nginexx -network my_network nginx



```

> Connect a Network

```
docker network  connect my_network| networkID  containerID|nginnexx
```

> Disconnect a Network

```
docker network  disconnect my_network| networkID  containerID|nginnexx
```

---

## Docker multiple hosting on the same server and port Reverse nginx.

---

### Docker network create nginx-proxy

---

> Docker-composer for reverse nginx server

```
version: "3"

services:
    nginx-proxy:
        image: jwilder/nginx-proxy
        container_name: nginx-proxy
        ports:
          - "80:80"
        volumes:
            - /var/run/dock.sock:/tmp/docker.sock:ro

netowrks:
    defualt:
        external:
          name: nginx-proxy
```

then :

```
Docker run -d —name blog —expose 80 —net nginx-proxy -e VIRTUAL_HOST=subdomain.domain.com image/name
```

> BY: Najah Said Ahmed
