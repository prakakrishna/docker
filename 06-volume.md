## Working with Docker Volumes

Docker volumes allow you to store data persistently and share data between containers. This guide will show you how to create, use, and manage Docker volumes with the volume name `demo`.

### 1. Create a Docker Volume

Create a Docker volume named `demo`:
```bash
docker volume create demo
```
### 2. Inspect the Volume

To view details about the created volume, use the `docker volume inspect` command:
```bash
docker volume inspect demo
```
### 3. Run a Container with a Volume

Run a container and mount the volume `demo` to a specific path within the container. For example, use an `nginx` container and mount the volume to `/usr/share/nginx/html`:
```bash
docker run -d --name web -v demo:/usr/share/nginx/html -p 8080:80 nginx
```
### 4. Write Data to the Volume

To write data to the volume, use another container to interact with the mounted volume. For example, use an `alpine` container to create an `index.html` file in the volume:
```bash
docker run --rm -it -v demo:/data alpine sh -c "echo '<h1>Hello, Docker Volume!</h1>' > /data/index.html"
```
### 5. Verify the Data

To verify the data written to the volume, you can use another container to check the contents of the `index.html` file:
```bash
docker run --rm -it -v demo:/data alpine cat /data/index.html
```
### 6. Access the Data via Web Browser or `curl`

To access the `index.html` file served by the `nginx` container, open your web browser and go to `http://localhost:8080`. You should see the content `Hello, Docker Volume!`.

Alternatively, you can use `curl` to verify the content from the command line:
```bash
curl http://localhost:8080
```
### 7. Remove the Volume

To remove the volume, ensure that no container is using it. Then, use the `docker volume rm` command:
```bash
docker volume rm demo
```
### 8. List Docker Volumes

To list all Docker volumes on your system, use:
```bash
docker volume ls
```
### Summary

1. Create a volume with `docker volume create demo`.
2. Inspect the volume with `docker volume inspect demo`.
3. Run a container and mount the volume using `docker run -v demo:/path`.
4. Write data to the volume using another container by creating an `index.html` file.
5. Verify the data by inspecting the `index.html` file from a different container.
6. Access the data via a web browser at `http://localhost:8080` or use `curl http://localhost:8080`.
7. Remove the volume with `docker volume rm demo`.
8. List all volumes with `docker volume ls`.

Docker volumes are a powerful feature for managing data persistence and sharing data between containers. They help ensure that data is preserved across container restarts and updates.
