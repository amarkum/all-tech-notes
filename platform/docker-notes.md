
# Docker Commands Guide

This guide provides essential Docker commands for building, tagging, pushing, pulling, and managing Docker images and containers. 

---

## I. Build a Docker Image

Docker images are the blueprints for containers. You can create them from a Dockerfile.

- **Build with Latest Tag**  
  Creates an image tagged with `latest` based on the Dockerfile in the current directory.
  ```bash
  docker build -t flask_webservice:latest .
  ```

- **Build with Custom Tag**  
  Creates an image from a specific Dockerfile (e.g., `Dockerfile.prod`) and tags it with a custom name.
  ```bash
  docker build -f Dockerfile.prod -t react-app:prod .
  ```

---

## II. Push the Docker Image

After building an image, it can be pushed to a registry like Docker Hub for sharing or deployment.

### Re-tag Docker Image

- **Latest Tag**  
  Re-tags `flask_webservice` image as `amarxcode/flask_webservice`.
  ```bash
  docker tag flask_webservice amarxcode/flask_webservice
  ```

- **Custom Tag**  
  Re-tags `sample:prod` as `amarxcode/sample:prod` for a custom deployment.
  ```bash
  docker tag sample:prod amarxcode/sample:prod
  ```

### Push the Image to Docker Hub

- **Custom Tag**  
  Pushes the custom-tagged `react-app:prod` image to Docker Hub.
  ```bash
  docker push amarxcode/react-app:prod
  ```

- **Latest Tag**  
  Pushes the latest `flask_webservice` image to Docker Hub.
  ```bash
  docker push amarxcode/flask_webservice
  ```

---

## Pull the Docker Image & Run

To pull an image from a registry (like GitLab) and run it.

```bash
docker pull registry.gitlab.com/amarxcode/flask_webservice
docker run registry.gitlab.com/amarxcode/flask_webservice
```

---

## Docker Common Commands

Common commands for listing images, removing containers, and cleaning up Docker.

- **List all Docker images**  
  ```bash
  docker image ls -a
  ```

---

## III. Remove Docker Images & Containers

- **Delete all containers (including volumes)**  
  Removes all stopped containers and associated volumes.
  ```bash
  docker rm -vf $(docker ps -a -q)
  ```

- **Delete all images**  
  Forcefully removes all Docker images.
  ```bash
  docker rmi -f $(docker images -a -q)
  ```

- **Kill all running containers**  
  Stops all currently running containers by ID.
  ```bash
  docker kill <container_id>
  ```

- **Remove all unused images, containers, networks, and build caches**  
  Cleans up Docker by removing unused items.
  ```bash
  docker system prune -a
  ```

--- 

This guide covers the basics and a few advanced Docker commands for image and container management, ensuring a smooth workflow in Docker environments.
