---
date: 2017-12-09 09:50:47+00:00
layout: post
title: 'docker reclaim disk'
categories: 技术
tags:  docker disk
---

[clearn disk] (https://lebkowski.name/docker-volumes/)


Cleaning up docker to reclaim disk space

#1 Good practices regarding keeping disk usage to a minimum



You can remove untagged images by running:
```
# hint osx users: your version of xargs won’t have the -r switch
# so just skip it (you may encounter an error if there are no
# images to clean up)

docker images --no-trunc | grep '<none>' | awk '{ print $3 }'   | xargs -r docker rmi
```

docker run leaves the container by default. This is convenient if you’d like to review the process later -- look at the logs or exit status. This also stores the aufs filesystem changes, so you can commit the container as a new image.

This can be expensive in terms of disk space usage, especially during testing. Remember to use docker run --rm flag if you don’t need to inspect the container later. This flag doesn’t work with background containers (-d), so you’ll be left with finished containers anyway. Clean up dead and exited containers using command:

```
docker ps --filter status=dead --filter status=exited -aq | xargs docker rm -v
```

# Docker filesystem storage and volumes

Now, since there is no tool to list volumes and their state, it’s easy to leave them on disk even after all processes exited and all containers are removed. The following command inspects all containers (running or not) and compares them to created volumes, printing only the paths that are not referenced by any container:

```
#!/usr/bin/env bash

find '/var/lib/docker/volumes/' -mindepth 1 -maxdepth 1 -type d | grep -vFf <(
  docker ps -aq | xargs docker inspect | jq -r '.[]|.Mounts|.[]|.Name|select(.)'
)
```

The command doesn’t remove anything, but simply passing the results to xargs -r rm -fr does so.

Hint: docker 1.9 has new volume management system, so it’s way easier with this version:
```
docker volume ls -qf dangling=true | xargs -r docker volume rm
```

Recap
```
#!/bin/bash

# remove exited containers:
docker ps --filter status=dead --filter status=exited -aq | xargs -r docker rm -v

# remove unused images:
docker images --no-trunc | grep '<none>' | awk '{ print $3 }' | xargs -r docker rmi

# remove unused volumes (needs to be ran as root):
find '/var/lib/docker/volumes/' -mindepth 1 -maxdepth 1 -type d | grep -vFf <(
  docker ps -aq | xargs docker inspect | jq -r '.[]|.Mounts|.[]|.Name|select(.)'
) | xargs -r rm -fr
```

