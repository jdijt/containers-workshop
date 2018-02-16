# Building Images

---
### Docker images

- Usually based on a Linux Distro.
- Created using a "DockerFile"
- One image can extend the other.

---
### Create an image.

- First: create a dockerfile in the repo root:
- Examples of instructions: `CMD`, `ENTRYPOINT`, `RUN`, `COPY`, `ENV`.

```
FROM nginx

ADD ./docs /usr/share/nginx/html
```

Note:
- Full list -> RTFM.


---
### Create an image

- Lets build it!:

```
docker build -t docker-presentation .
```

Note:
- What happens here?!
- Docker actually runs a container, and executes the steps, and then saves the results.

---
### Image layers.

- Each instruction in a dockerfile results in a new layer.
- Layers can be shared accross images.
    - Most easily by using "FROM" 
    - Or: Further extending an image.

---
### Extending docker-presentation

- Lets make the port our presentation listens on configurable.
- This is done via environment variables.
- Lets implement!
    - Use ADD and RUN.
    - Use ENV to set a default.
    - `envsubst` for replacing the value.
    - nginx expects the config in `/etc/nginx/sites-available`.

Note:
- Lets code this together.
- Point to repo file.
- Explain 'envsubst'
- What happens when we build it?
- Does the order matter? -> Not for funtionality, does for build and layer reuse.

---
### Sharing docker-presentation
