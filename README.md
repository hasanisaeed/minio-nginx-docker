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
    > This command create your `s3` container. Check it with `docker ps` command.


# Nginx
## Step 4: Create subdomain
Open `/etc/host` file and add your subdomain:
> 127.0.0.1       localhost 
>
> 127.0.0.1       s3.localhost # You can rename `s3` with desiered name.

So at `/etc/nginx/sites-enabled/default` edit server_name key as `s3.localhost`.

    ```bash
    // add this block at the end of `default` file:
    server {
        listen 80;
        listen [::]:80;

        server_name s3.localhost;

        index index.html;

        location / {
            proxy_pass http://127.0.0.1:9001/;
        }
    }
    ```

Then restart nginx:

    ```bash
    sudo service nginx reload
    ```

 # Run MinIO
 Go to your browser and open [http://s3.localhost](s3.localhost).
 
 Username and password is in `.env` file. Login and create your `Buckets`.

