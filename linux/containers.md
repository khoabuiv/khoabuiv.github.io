---
layout: post
---

# Containers 

- **Docker** is an application-level virtualization using many individual images to build up the necessary services to support the target application.
- Docker image components:
    - Application code​
    - Runtime libraries​
    - System tools​
Docker is that an application can be packaged up with all of its dependent code and services and deployed as a single unit with the minimum of overhead. 
- **docker compose**: allows you to specify runtime as well as build time configuration details for Docker containers using a YAML docker-compose.yml file.


## How to build and run a container?
1. Create a Docker file with the following name <name>.Dockerfile with the content:
```
FROM [initializes a new build stage and sets the base image for subsequent instructions]
RUN [execute any commands to create a new layer on top of the current image]
CMD [sets the command to be executed when running a container from an image]
```
2. Build the container:
```
docker build  -f <name>.Dockerfile -t <tag-list>
```
3. Run the container:
```
docker run --rm httpie
```