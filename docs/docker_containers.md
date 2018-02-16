# Docker Containers

---
### Docker on the Mac.

- Docker cannot run natively on the Mac
- Docker for Mac runs a Linux VM

---
### Isolation in Docker

- Mount
- Processes
- Network stack
- Users

Note:
- Demonstrate using example1.
- Users requires special setup, we'll not explain here. Generally should not concern app developers as ops should fix that.

---
### Docker Containers

- Based on a "Docker image".
- Geared towards one app per container.
- Should be ephemeral.

Note:
- Image contains all non kernel dependencies.
- one app: e.g.: capturing stdout/stderr, process control must be implemented in container.
- one app: e.g.: API Server; Database; Memcache; Static asset serving: all in separate containers behind a proxy (another container).
- ephemeral: e.g.: can be destroyed and rebuilt with minimal setup & config. No state inside the container.
- ephemeral: Containerizing a DB server? -> can be done, needs special magic to keep data, dicuss later.

---
### Running a Docker container

Example: Lets run a webserver!

```
cd <repo root>
docker run -d nginx
```

Note:
- What happens here?
    - The image gets fetched, if needed.
    - It starts.
- Problem: we cannot access it easily.
    - Try to anyway..

---
### Aside: Docker hub

- Where does this "nginx" come from?
- The Docker Hub: https://hub.docker.com
- Contains prebuilt images you can run, or base your images on.
    - e.g.: nginx, ubuntu..

Note:
- Can also make images from scratch -> advanced topic.
- Private registries also exist.
- Creating your own registry on docker hub also possible.
- Extending these images will be discussed later.

---
### Running a Docker container.

- Add a port mapping for easy access. 

```
docker run -d -p8080:80 nginx
```

Note:
- Go to localhost:8080!
- Or: <docker-machine-ip>:8080

---
### Running a Docker container.

- Some content would be nice.
- Lets just mount it into the container:

```
docker run -d -p8080:80 -v${PWD}/docs:/usr/share/nginx/html nginx
```

Note:
- That didn't work, why?
    - Lets fix that.
    - Shared vs unshared resources.
- Wait what, how can I mount Mac folders into the linux VM? -> Docker for mac magic.

---
### Managing containers.

- `docker ps` - Get a list of running container.
- `docker kill <container name>` - Terminate a container.
- `docker rm <container name>` - Remove a container.
- `docker run <container name>` - Start a container.

Note:
- There be more, RTFM.

---
### Inspecting a running container

- What information can we extract about our nginx container?
- `docker logs <container name>` - Read the output from a container.
- `docker exec -ti <container name> <command>` - Run something inside a container.
- `docker container <subcommands>` - 

Note:
- Look around a bit.
- Edit presentation, wut?

---
### Read only volumes

- Volumes can be mount read only.
- This prevents you from trashing files.

```
docker run -p8080:80 -v${PWD}/docs:/usr/share/nginx/html:ro nginx
```
