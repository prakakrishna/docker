# Hands-on with Docker Hello World Image

## Steps to Run Docker "Hello World" Image

1. **Verify Docker Installation**:
   Open your terminal (or command prompt) and type:
   ```bash
   docker --version
   ```

2. **Pull and Run the Hello World Image**:
   Run the following command to pull and run the "hello-world" container:
   ```bash
   docker run hello-world
   ```

3. **Check the Output**:
   Docker will download the image (if not already present) and run it. You should see output like this:
   ```bash
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   ```

4. **List Docker Images**:
   To check if the image is present locally:
   ```bash
   docker images
   ```

5. **Remove Exited Container**:
   If the `hello-world` container is still present in an "Exited" state, you can remove it by running:
   ```bash
   docker ps -a
   docker rm [CONTAINER_ID]
   ```
   Replace `[CONTAINER_ID]` with the actual ID of the container.

6. **Clean Up (Optional)**:
   If you want to remove the "hello-world" image:
   ```bash
   docker rmi hello-world
   ```

This guide demonstrates how Docker pulls an image from Docker Hub, runs it, and displays a message.
