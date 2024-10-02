# Docker Commands

1.  **Pull an image from Docker Hub**:

    ```bash
    docker pull image_name
    ```
2.  **Run a Docker container**:

    ```bash
    docker run image_name
    ```

    Add `-d` for detached mode, `-p` to map ports, and `--name` to give the container a name:

    ```bash
    docker run -d -p host_port:container_port --name container_name image_name
    ```
3.  **List running containers**:

    ```bash
    docker ps
    ```
4.  **List all containers (including stopped)**:

    ```bash
    docker ps -a
    ```
5.  **Stop a running container**:

    ```bash
    docker stop container_name_or_id
    ```
6.  **Remove a stopped container**:

    ```bash
    docker rm container_name_or_id
    ```
7.  **Remove an image**:

    ```bash
    docker rmi image_name
    ```
8.  **Build an image from a Dockerfile**:

    ```bash
    docker build -t image_name .
    ```
9.  **Check logs of a container**:

    ```bash
    docker logs container_name_or_id
    ```
10. **Exec into a running container** (open bash inside a container):

    ```bash
    docker exec -it container_name_or_id /bin/bash
    ```
11. **View all images**:

    ```bash
    docker images
    ```
12. **Remove dangling/unused images**:

    <pre class="language-bash"><code class="lang-bash"><strong>docker image prune
    </strong></code></pre>
13. **Start a stopped container**:

    ```bash
    ocker start container_name_or_id
    ```
14. **Stop and remove all containers**:

    ```bash
    docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)
    ```

