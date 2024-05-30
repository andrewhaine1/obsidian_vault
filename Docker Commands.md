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

Docker remove dangling images
```
docker rmi $(sudo docker images -f "dangling=true" -q)
```
