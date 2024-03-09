# Docker Cheat Sheet

## INSTALLATION

- **Docker Desktop** is available for Mac, Linux, and Windows: [https://docs.docker.com/desktop](https://docs.docker.com/desktop)
- View example projects that use Docker: [https://github.com/docker/awesome-compose](https://github.com/docker/awesome-compose)
- Check out our docs for information on using Docker: [https://docs.docker.com](https://docs.docker.com)

## GENERAL COMMANDS

- **Start the docker daemon:**

```shell
docker -d
```
- **Docker help:**

```shell
docker --help
```

- **Display system-wide information:**

```shell
docker info
```

- **Display system-wide information:**

```shell
docker --help
```

- **Build an image from a Dockerfile:**

```shell
docker build -t <image_name> <path-to-Dockerfile>
docker build -t foobar .
```

- **Build an image with a tag:**

```shell
docker build -t <image-name>:<tag> <path-to-Dockerfile>
docker build -t foobar:v1 .
```

- **Build an Image from a Dockerfile without the cache:**

```shell
docker build -t <image_name> . --no-cache
docker build -t foobar:v1 . --no-cache

```

- **Delete an Image:**

```shell
docker rmi <image_name>
docker rmi foobar
```

- **Delete an Image:**

```shell
docker rmi <image_name>
docker rmi foobar
```

## IMAGES COMMANDS

- **Remove all unused images**

```shell
docker image prune
```

- **Delete all docker images:**

```shell
docker rmi $(docker images -a -q)
```
## CONTAINERS COMMANDS

- **Create and run a container from an image, with a custom name:**

```shell
docker run --name <container_name> <image_name>
docker run --name myapp foobar
```
- **Run a container and publish a container’s port(s) to the host:**

```shell
docker run -p <host_port>:<container_port> <image_name>
docker run -p 8080:5000 foobar
```

- **Run a container in the background (detached mode):**

```shell
docker run -d <image_name>
```

- **Start or stop an existing container:**

```shell
docker start|stop <container_name> (or <container_id>)
```

- **Remove a stopped container:**

```shell
docker rm <container_name>
```

- **Open a shell inside a running container:**

```shell
docker exec -it <container_name> sh
```

- **Fetch and follow the logs of a container**

```shell
docker logs -f <container_name>
```

- **To list currently running containers:**

```shell
docker ps
```

- **List all docker containers (running and stopped):**

```shell
docker ps --all
```

- **View resource usage stats:**

```shell
docker container stats
```

## DOCKERFILE

```
FROM: Specifies the base image.
RUN: Executes commands in a new layer on top of the current image.
CMD: Provides defaults for executing a container.
LABEL: Adds metadata to an image.
EXPOSE: Indicates the ports on which a container listens.
ENV: Sets environment variables.
ADD: Copies new files, directories, or remote file URLs.
COPY: Copies new files or directories.
ENTRYPOINT: Configures a container that will run as an executable.
VOLUME: Creates a mount point with the specified name.
USER: Sets the user name or UID.
WORKDIR: Sets the working directory.
ARG: Defines a variable that users can pass at build-time.
```

- Example Dockerfile:

```
# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Define build-time environment variable
ARG APP_PORT=5000

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file
COPY requirements.txt ./

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application source code
COPY . .

# Use ARG value to set a runtime environment variable
ENV PORT=$APP_PORT

# Expose the application port
EXPOSE $PORT

# Run the application
CMD ["python", "./your-app.py"]

```

![Docker](/pic/1709962727255.gif) 
