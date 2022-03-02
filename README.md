Configuration for MinIO with Nginx on Docker 

----
- Create `minio` user
    ```bash
    sudo useradd minio
    ```

- You then add a password for the `minio` user by using the `passwd` command:

    ```bash
    sudo passwd minio
    ```

- Make minIO directory and change owner to `minio` user:


    ```bash
    mkdir -p /usr/local/share/minio
    sudo chown -R minio:minio /usr/local/share/minio
    ```

- Create docker container with:

    ```bash
    docker-compose up -d --build
    ```
