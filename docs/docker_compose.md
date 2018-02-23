# Composing Docker Containers

---
### Docker Compose

- Run several related containers using one command.
- Scale these containers indepentently.

---
### Anatomy of a compose file

- Name: `docker-compose.yml`
- Contains:
    - `version` - The version of docker-compose to use (commonly: 3)
    - `services` - List of containers to run.

---
### Services

- Like a `docker run` command, but in yaml.
- Contains:
    - Port mappings
    - Volumes
    - Environment
    - Image/tag to use
    - Command to run.
- Services can refer to other services by name.

---
### Lets compose something

- In the repo move to the `compose` directory.
- We will fill out the compose file.
- There are two services to fill out, countries, airports.
    - Airports image: `jdijt/api1:1.0.0`
    - Countries image: `jdijt/api2:1.0.0`
    - Both listen on port 8080.
    - Both are to be exposed via the nginx proxy defined in the compose file.

---
### Improving the compose file.

- Networks
- Dependencies
    - Start your containers in the right order
- Scaling
    - Caveat: volumes & portmappings


---
### A more complicated example

- Complete dev setup for a project (Lunatech University).
