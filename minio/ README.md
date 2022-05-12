## What is minio?

MinIO offers high-performance, S3 compatible object storage.
Native to Kubernetes, MinIO is the only object storage suite available on
every public cloud, every Kubernetes distribution, the private cloud and the
edge. MinIO is software-defined and is 100% open source under GNU AGPL v3.

## Environment

|                |                    version                    |
| :------------: | :-------------------------------------------: |
|     docker     |     Docker version 20.10.7, build f0df350     |
| docker-compose | docker-compose version 1.26.2, build eefe0d31 |
|     minio      |                    latest                     |

## Docker-compose.yml

```
version: "3.1"

services:
  minio:
    image: minio/minio:latest
    container_name: minio
    restart: always
    ports:
      - 19000:9000
      - 19001:9001
    command: server /data --console-address ":9001"
    environment:
      MINIO_ACCESS_KEY: username
      MINIO_SECRET_KEY: password
    volumes:
      - ./data:/data

```
