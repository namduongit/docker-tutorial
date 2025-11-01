**1. Pull MYSQL image**
- Select Mysql:[tag] from Docker Hub
- URL: https://hub.docker.com/_/mysql
```bash
docker pull mysql:latest

# Verify image is downloaded
docker images mysql

# Output:
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
mysql        latest    5f4dcc3b5aa6   2 weeks ago   544MB
``` 

**2. Run MYSQL container**
```bash
docker run \
    --name mysql-container \
    -e MYSQL_ROOT_PASSWORD=my-secret-pw -e MYSQL_DATABASE=mydatabase \
    -p 3306:3306 \
    -v mysql-data:/var/lib/mysql \
    -d mysql:latest
```

- Explanation:
    + `--name mysql-container` : Assign a name to the container
    + `-e MYSQL_ROOT_PASSWORD=my-secret-pw` : Set environment variable for root password
    + `-e MYSQL_DATABASE=mydatabase` : Set environment variable to create a database
    + `-p 3306:3306` : Publish container's port 3306 to host's port 3306
    + `-v mysql-data:/var/lib/mysql` : Bind mount a volume for MySQL data persistence
    + `-d` : Run container in background and print container ID
    + `mysql:latest` : Use the latest MySQL image

**3. Verify MYSQL container is running**
```bash
docker ps
```     

**4. Connect to MYSQL container**
```bash
docker exec -it mysql-container mysql -uroot -p my-secret-pw
```

