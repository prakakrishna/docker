# Working with Docker Volumes and Host File Sharing

Docker allows you to mount host directories inside containers, enabling data sharing between the host and containers. 
This guide will show you how to use Docker volumes and bind mounts to share a host folder (`/opt/web`) with a container.

## 1. Prepare the Host Directory

Ensure that the host directory `/opt/web` exists and has the necessary files. If it doesn't exist, create it and add some content:
```bash
mkdir -p /opt/web  
echo '<h1>Hello from Host Directory!</h1>' > /opt/web/index.html
```
## 2. Run a Container with Host Directory Sharing

Run a container and mount the host directory `/opt/web` to a specific path inside the container, such as `/usr/share/nginx/html`:
```bash
docker run -d --name web -v /opt/web:/usr/share/nginx/html -p 8080:80 nginx
```
Here, `-v /opt/web:/usr/share/nginx/html` mounts the host folder `/opt/web` to `/usr/share/nginx/html` inside the container.

## 3. Verify the Data

To verify that the data from the host folder is shared with the container, open a web browser and visit `http://localhost:8080`. 
You should see the content `Hello from Host Directory!`.

Alternatively, use `curl` to confirm the content from the command line:
```bash
curl http://localhost:8080
```
## 4. Modify Data on the Host

You can modify the files in `/opt/web` on the host machine, and the changes will be reflected in the container. 
For example, update the `index.html` file:
```bash
echo '<h1>Updated Content from Host!</h1>' > /opt/web/index.html
```
Refresh the web page at `http://localhost:8080`, and you should see the updated content.

## 5. Clean Up

To stop and remove the container, use the following commands:
```bash
docker stop web  
docker rm web
```
You can keep or remove the host folder `/opt/web` as needed:
```bash
rm -rf /opt/web
```
## Summary

1. Create or prepare a host folder (`/opt/web`) and add content.
2. Run a container and bind the host folder to a container path using `docker run -v /opt/web:/path`.
3. Access the data via a web browser at `http://localhost:8080` or use `curl http://localhost:8080`.
4. Modify the host folder contents, and the changes will reflect in the container.
5. Clean up by stopping and removing the container and folder.
