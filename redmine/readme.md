# Redmine

## Preparation

```
# docker-machine.exe ssh default 'sudo mkdir /d' \
# && docker-machine.exe ssh default 'sudo mount -t vboxsf -o uid=0,gid=0 d /d'
cd /d/dockerp/redmine

docker-compose up
```
## services

* postgresql
* redmine
* data container (busybox)

redmine http://192.168.99.100:3001

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