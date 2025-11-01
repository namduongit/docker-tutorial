**1. Pull POSTGRES image**
- Select Postgres:[tag] from Docker Hub
- URL: https://hub.docker.com/_/postgres
```bash
docker pull postgres:latest

# Verify image is downloaded
docker images postgres

# Output:
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
postgres     latest    3c4a6f4f1b2e   2 weeks ago   374MB
```

**2. Run POSTGRES container**
```bash
docker run \
    --name postgres-container \
    -e POSTGRES_PASSWORD=my-secret-pw -e POSTGRES_DB=mydatabase \
    -p 5432:5432 \
    -v postgres-data:/var/lib/postgresql/data \
    -d postgres:latest
```

- Explanation:
    + `--name postgres-container` : Assign a name to the container
    + `-e POSTGRES_PASSWORD=my-secret-pw` : Set environment variable for postgres password
    + `-e POSTGRES_DB=mydatabase` : Set environment variable to create a database
    + `-p 5432:5432` : Publish container's port 5432 to host's port 5432
    + `-v postgres-data:/var/lib/postgresql/data` : Bind mount a volume for Postgres data persistence
    + `-d` : Run container in background and print container ID
    + `postgres:latest` : Use the latest Postgres image


**3. Verify POSTGRES container is running**
```bash
docker ps
```

**4. Connect to POSTGRES container**
```bash
docker exec -it postgres-container psql -U postgres -d mydatabase
```