# Docker Hands-on with Nginx

## 1. Pull the Nginx Image

First, ensure you have Docker installed and running. Then, pull the latest Nginx image from Docker Hub:

```bash
docker pull nginx
```

## 2. Run an Nginx Container

To run an Nginx container with the following parameters:

- **Container Name:** `web`
- **Published Port:** 80 (maps container port 80 to host port 80)

Use the following command:

```bash
docker run --name web -p 80:80 -d nginx
```

### Breakdown of the Command:

- `--name web`: Assigns the name `web` to the container.
- `-p 80:80`: Maps port 80 on the host to port 80 on the container.
- `-d`: Runs the container in detached mode.
- `nginx`: Specifies the image to use.

## 3. Verify the Running Container

Check if the container is running with:

```bash
docker ps
```

You should see output similar to:

```text
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                NAMES
xxxxxxxxxxxx   nginx     "/docker-entrypoint.…"   x seconds ago   Up x seconds   0.0.0.0:80->80/tcp   web
```

## 4. Access Nginx

Open a web browser and navigate to `http://localhost`. You should see the default Nginx welcome page.

## 5. Cleanup

To stop and remove the Nginx container, execute:

```bash
docker stop web
docker rm web
```

To remove the Nginx image (if you no longer need it):

```bash
docker rmi nginx
```

## Summary

- **Pull the Image:** `docker pull nginx`
- **Run the Container:** `docker run --name web -p 80:80 -d nginx`
- **Verify Running Container:** `docker ps`
- **Stop and Remove Container:** `docker stop web` and `docker rm web`
- **Remove Image:** `docker rmi nginx`
