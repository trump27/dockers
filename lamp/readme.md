# LAMP

## Preparation

```
docker-machine.exe ssh default 'sudo mkdir /d' \
&& docker-machine.exe ssh default 'sudo mount -t vboxsf -o uid=0,gid=0 d /d'
cd /d/dockerp/lamp

docker-compose up
```

## services

* mariadb
* phpmyadmin
* apache / php (centos6)
* data container (busybox)

index.php http://192.168.99.100/index.php
phpmyadmin http://192.168.99.100:8080

## sample commands

```
# at first
docker-compose up / create
docker-compose stop

# restart
docker-compose start

# remove containers
docker-compose rm
docker-compose down
```


## remove containers and images

```
docker rm `docker ps -a -q` \
&& docker rmi $(docker images -a | awk '/^<none>/ { print $3 }')
```