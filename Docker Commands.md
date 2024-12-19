Show docker storage status
```
docker system df
```

Get reclaimable space
```
docker system prune -a
```

Remove all docker containers
```
docker rm -v -f $(docker ps -qa)
```

Prune volumes only
```
docker volume prune
```

Remove all docker images
```
docker rmi -f $(docker images -aq)
```

To delete all containers including its volumes use
```
docker rm -vf $(docker ps -aq)
```

Remove all docker containers and images 
```
docker rm -v -f $(docker ps -qa) && docker rmi -f $(docker images -aq)
```

Docker ps format table
```
docker ps --format "table {{.Image}}\t{{.Names}}"
```

Docker ps names, ids, and images
```
docker ps --format "table {{.Names}}\t{{.ID}}\t{{.Image}}"
```

Docker container ls format table
```
docker container ls --format 'table {{.ID}}\t{{.Names}}\t{{.Image}}'
```

Docker remove dangling images
```
docker rmi $(sudo docker images -f "dangling=true" -q)
```

Change file line endings for docker script execution
Common issue on Windows - just change line endings.
Open terminal eq. git bash
```
Run dos2unix ./* to convert line endings
```
Rebuild and restart docker image

Import repos for microk8s
```
for repo in $(docker image ls --format '{{.Repository}}');do imagename=${repo#*/};docker save $repo > "$imagename.tar";microk8s ctr image import "$imagename.tar";done
```
