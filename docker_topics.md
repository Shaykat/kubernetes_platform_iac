# Docker Installation CLI/Desktop
  - Install it from the [docker](https://docs.docker.com/desktop/setup/install/mac-install/)

# Understanding Image vs Container
  - Docker image is a set of instructions
  - Docker container is an isolation of computer process where a docker image runs and creates the virtual environment.
  - Docker container is a result of execution of the instructions contained in a docker image.

# Running ubuntu Image in Container
  - ```docker run -it ubuntu```

# Docker Logs
  - ```docker logs minio```

# Multiple Containers

# Port Mapping

# Environment Variables

# Dockerization of a nodejs Application
  - Dockerfile
  - Caching Layers
  - Publishing to Hub

# Docker Networking
  - Bridge
  - Host
  - None

# Volume Mounting
  - Mount a host directory with a single container 
  - Mount a host directory with multiple container

# Efficient Caching in Layers
  - Each steps of the Docker file is called a layer. 
  - For example: ```From ubuntu``` it is a layer. ```RUN copy app /app``` this is another layer.

# Docker Multi-Stage Builds
  - Docker build commands builds the whole image file at the first build and chach it.
  - From the second build if nothing changes it will build in seconds because it will take it from the cache
  - From the second build if anything changes it will start rebuild from the layer where the change happened.
  - So we should order the layers of the docker image in such a way that 
    - It keeps the less frequently changed contents in the top layer compared to the more frequently changed
    - For example: We change the project dependency like libbraries to be installed less frequently and change the code base more frequently. So it is better to keep the installation parts at the beginging and code base copy layer more down the line.

# Docker Compose 
  - Services
  - Port Mapping
  - Env Variables
  - ```docker-compose up -d```
  - ```docker-compose down```
  - ```docker-compose stop```
  - ```docker-compose logs minio```
  - ```docker-compose logs -f minio```

# Running a Postgres Instance in a Docker Container
  - ```docker pull postgres```
  - ```docker run --name sh-postgres -p 5432:5432 -e POSTGRES_PASSWORD=admin -d postgres```

# Running a Minio Inastance in Docker Container with Volume
  - ```docker pull minio/minio```
  - Run a minio instance in a docker container and attach a volume to the container to store the data persistantly 
    ```docker run -dt \
      -p 9000:9000 -p 9001:9001 \
      -v /Users/shaykatmdabdulmutalab/Documents/Development/kubernetes_platform_iac/data:/mnt/data \
      -e "MINIO_CONFIG_ENV_FILE=/Users/shaykatmdabdulmutalab/Documents/Development/kubernetes_platform_iac/config.env" \
      --name "minio" \
      minio/minio:latest server /mnt/data --console-address ":9001"```
