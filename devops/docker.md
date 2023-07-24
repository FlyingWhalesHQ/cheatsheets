---
layout: default
title: Docker
parent: Devops
---

{% include toc.md %}

## Prune

Prune images

```sh
# clean up dangling images
docker image prune

# clean up all images which are not used by existing containers
docker image prune -a

# options
# --force or -f : bypass confirmation prompt
# --all or -a : remove all unused images
# --filter : filter images, e.g. --filter "until=24h" to filter images older than 24h
```

Prune containers, volumes, network

```sh
# remove stopped containers
docker container prune

# remove unused volumes
docker volume prune

# remove unused networks
docker network prune

# options
# --force or -f : bypass confirmation prompt
# --filter : filter containers/volumes/networks, e.g. --filter "until=24h"
# to filter containers/volumes/networks older than 24h
```

Prune everything

```sh
# remove dangling images, stopped containers, unused networks, build caches
docker system prune

# options
# --force or -f : bypass confirmation prompt
# --volumes : remove unused volumes
```
