Configuration for MinIO with Nginx on Docker 

## Step 1: Create minio user
- Create `minio` user
    ```bash
    sudo useradd minio
    ```

- You then add a password for the `minio` user by using the `passwd` command:

    ```bash
    sudo passwd minio
    ```
## Step 2: Create shared folder
- Make minIO directory and change owner to `minio` user:


    ```bash
    mkdir -p /usr/local/share/minio
    sudo chown -R minio:minio /usr/local/share/minio
    ```
## Step 3: Create docker container:
- Create docker container with:

    ```bash
    docker-compose up -d --build
    ```
