# Docker Hands-On with Nginx: Multiple Containers

In this guide, we will set up three Nginx containers running on different ports using Docker. We will also cover cleanup steps to remove the containers and images afterward.

## Step-by-Step Guide

### 1. Run Nginx Containers

We will run three Nginx containers, each serving on different ports.

#### Container `web-1` on port `8081`
```bash
docker run -d --name web-1 -p 8081:80 nginx
```
#### Container `web-2` on port `8082`
```bash
docker run -d --name web-2 -p 8082:80 nginx
```
#### Container `web-3` on port `8083`
```bash
docker run -d --name web-3 -p 8083:80 nginx
```
### 2. Verify the Setup

To check if the containers are running:
```bash
docker ps
```
You should see `web-1`, `web-2`, and `web-3` with the corresponding ports mapped to `8081`, `8082`, and `8083`.

### 3. Access Nginx Web Servers

Open your browser and navigate to the following URLs to see the default Nginx page served by each container:

- http://localhost:8081
- http://localhost:8082
- http://localhost:8083

### 4. Cleanup

After verifying that everything is working, you can clean up the Docker containers.

#### Stop and Remove Containers
```bash
docker stop web-1 web-2 web-3
docker rm web-1 web-2 web-3
```
#### Remove Docker Images (Optional)

If you want to remove the Nginx images (though they will be re-pulled if needed):
```bash
docker rmi nginx
```
## Summary

You have successfully set up multiple Nginx containers using Docker, each listening on a different port. This setup allows you to test multiple web server instances simultaneously on different ports. 

## Options Description

- `-d`: Runs the container in detached mode (in the background).
- `--name <name>`: Assigns a name to the container, which can be used for management purposes.
- `-p <host_port>:<container_port>`: Maps a port on the host to a port on the container. This allows you to access the service running inside the container via the host's port.
- `nginx`: Specifies the image to use for the container. In this case, it's the official Nginx image.
