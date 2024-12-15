# Postgres Docker Commands
$ docker pull postgres
$ docker run --name sh-postgres -p 5432:5432 -e POSTGRES_PASSWORD=admin -d postgres

# Minio Docker Commands
$ docker pull minio/minio
$ docker run -dt \
  -p 9000:9000 -p 9001:9001 \
  -v /Users/shaykatmdabdulmutalab/Documents/Development/kubernetes_platform_iac/data:/mnt/data \
  -e "MINIO_CONFIG_ENV_FILE=/Users/shaykatmdabdulmutalab/Documents/Development/kubernetes_platform_iac/config.env" \
  --name "minio" \
  minio/minio:latest server /mnt/data --console-address ":9001"

$ docker logs minio


# Docker Compose Commands
$ docker-compose up -d
$ docker-compose logs minio
$ docker-compose logs -f minio

$ docker-compose down
$ docker-compose stop

