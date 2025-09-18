# Distroless Docker Image Example

This project demonstrates how to build and run a container using a **Distroless** Docker image.

## What is Distroless?

Distroless images contain only your application and its runtime dependencies. They do **not** contain package managers, shells, or any other programs you would expect to find in a standard Linux distribution. This makes them smaller and more secure.

## How to Build and Run

1. **Navigate to the `helloworld` directory (Dockerfile and app.go are inside it):**

   ```sh
   cd helloworld
   ```

2. **Build the Docker image:**

   ```sh
   docker build -t my-distroless-app .
   ```

3. **Run the container (it will exit after printing):**

   ```sh
   docker run --name distroless-demo my-distroless-app
   ```

4. **List all containers (including exited ones):**

   ```sh
   docker ps -a
   ```

5. **View the output using `docker logs`:**

   ```sh
   docker logs distroless-demo
   ```

   You should see:
   ```
   Hello, world!
   ```

   > **Note:** The container will exit immediately after printing the message. This is expected for programs that finish execution.

## Why can't I exec into a distroless container?

Distroless images do **not** include a shell like `/bin/sh` or `/bin/bash`.  
If you try to exec into the container with a shell, you will get an error:

```sh
docker exec -it distroless-demo sh
```

**Output:**
```
exec: "sh": executable file not found in $PATH
```

This is expected and demonstrates the minimal, secure nature of distroless images.

## Cleanup

To remove the container after you are done:

```sh
docker rm distroless-demo
```

## Why Use Distroless?

- **Smaller image size**
- **Reduced attack surface**
- **Faster startup times**

---

<p align="right"><b>Keep calm and code on! 💻🚀</b></p>