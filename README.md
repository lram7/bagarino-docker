# Docker image to run Bagarino as server 

## TL;DR, I just want an instance up-and-running

Install [Docker](https://docs.docker.com/installation/).
Note: On OS X I recommend to follow [this](http://viget.com/extend/how-to-use-docker-on-os-x-the-missing-guide) guide. Chris knows what he is doing!

Launch Bagarino docker image
```
docker run -d -v ~/bagarino/:/bagarino-volume -p 8080:8080 -p 9000:9000 -p 35729:35729 -p 4022:22 -u jhipster -t bagarino-0.2.1
```
or 
```
docker run -i -p 8080:8080 -p 9000:9000 -p 35729:35729 -p 4022:22 -t bagarino /bin/bash
```

## Test the instance

From your client machine open your browser to localhost:8080/admin

Note: if you run docker within a VM (e.g. VirtualBox, Vagrant, etc) your client is within the VM itself. If you want to connect from your physical machine, verify VM settings are forward ports to it.

## Containers

Bagarino is running using 2 containers. One for the Postgres DB and one for the Java server. Data are persisted on the client volume.

Notes:
* If you want to integrate a container with a [host process manager](http://docs.docker.io/use/host_integration/), start the daemon with `-r=false` then use `docker start -a`.

* If you want to expose container ports through the host, see the [exposing ports](https://github.com/wsargent/docker-cheat-sheet#exposing-ports) section.


### Info

* [`docker ps`](http://docs.docker.io/reference/commandline/cli/#ps) shows running containers.
* [`docker inspect`](http://docs.docker.io/reference/commandline/cli/#inspect) looks at all the info on a container (including IP address).
* [`docker logs`](http://docs.docker.io/reference/commandline/cli/#logs) gets logs from container.
* [`docker events`](http://docs.docker.io/reference/commandline/cli/#events) gets events from container.
* [`docker port`](http://docs.docker.io/reference/commandline/cli/#port) shows public facing port of container.
* [`docker top`](http://docs.docker.io/reference/commandline/cli/#top) shows running processes in container.
* [`docker diff`](http://docs.docker.io/reference/commandline/cli/#diff) shows changed files in the container's FS.

`docker ps -a` shows running and stopped containers.

### Entering a Docker Container

I know using an `sshd` daemon is [considered evil](http://jpetazzo.github.io/2014/06/23/docker-ssh-considered-evil/), but, as of today, I still you this method.

More info could be found at the [docker-cheat-sheet](https://raw.githubusercontent.com/wsargent/docker-cheat-sheet/master)
