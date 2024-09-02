## Connecting Containers on the Default Bridge Network

Connecting Docker containers using the default bridge network requires using IP addresses, as the default bridge network does not provide automatic DNS resolution for container names. Follow these steps to set up and connect containers:

### 1. Run the First Container

Start the first container. For example, use an `nginx` container:
```bash
docker run -d --name web nginx
```
### 2. Find the Container's IP Address

Retrieve the IP address of the `web`:
```bash
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' web
```
To get the entire json to inspect:
```bash
docker inspect web
```
### 3. Run the Second Container

Start the second container and use the IP address obtained in the previous step to communicate with the first container. For example, using a `curl` container:
```bash
docker run -it --rm curlimages/curl curl http://<web-ip>
```
Replace `<web-ip>` with the IP address you obtained from the `inspect` command.

### 4. Access Containers Interactively

To access a container interactively for debugging purposes, use the `bash` command. For example, to open a shell in the `curlimages/curl`:
```bash
docker run -it --rm curlimages/curl /bin/bash
```
You will see an interactive shell. Run the curl command from the shell
```bash
$ curl http://<web-ip>
```
### Summary

1. Run the first container with `docker run -d --name container1 ...`.
2. Find its IP address using `docker inspect`.
3. Run the second container and use the IP address for communication.
4. Use `docker exec` to access containers interactively if needed.

By following these steps, you can connect and communicate between Docker containers on the default bridge network. However, using a user-defined network is generally more convenient for container-to-container communication.
