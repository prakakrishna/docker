## Connecting Containers on a User-Defined Network

Using a user-defined network, such as `demo`, allows Docker containers to communicate by name and simplifies network management. Follow these steps to set up and connect containers on the `demo` network:

### 1. Create a User-Defined Network

Create the `demo` network:
```bash
docker network create demo
```
### 2. Run the First Container

Start the first container and connect it to the `demo` network. For example, use an `nginx` container with the name `web`:
```bash
docker run -d --name web --network demo nginx
```
### 3. Run the Second Container

Run the second container on the same `demo` network. For instance, use a `curl` container to test connectivity to the `web` container:
```bash
docker run -it --rm --network demo curlimages/curl curl http://web
```
### 4. Access Containers Interactively

To access a container interactively for debugging purposes, use the `bash` command. For example, to open a shell in the `curlimages/curl`:
```bash
docker run -it --rm curlimages/curl /bin/bash
```
You will see an interactive shell. Run the curl command from the shell
```bash
$ curl http://web
```

### Summary

1. Create the network with `docker network create demo`.
2. Run the first container with `docker run -d --name web --network demo ...`.
3. Run the second container and use container names for communication.
4. Use `docker exec` to access containers interactively if needed.

By using a user-defined network, Docker containers can communicate easily using container names, which is more convenient compared to using the default bridge network.
