## What is etcd?
etcd is a strongly consistent, 
distributed key-value store that provides a 
reliable way to store data that needs to be 
accessed by a distributed system or cluster of machines. 
It gracefully handles leader elections during network partitions 
and can tolerate machine failure, 
even in the leader node.

## Environment

|       | version |
|:------:|:-------:|
| docker |   Docker version 20.10.7, build f0df350      |
|   docker-compose     |  docker-compose version 1.26.2, build eefe0d31       |
|   etcd image     |    quay.io/coreos/etcd:v3.5.2     |

## Docker-compose.yml
- This is Single-node configuration
```
version: "3"
services:
  etcd:
    image: quay.io/coreos/etcd:v3.5.2
    container_name: etcd
    restart: always
    ports:
    - "12379:2379"
    environment:
    - ALLOW_NONE_AUTHENTICATION=yes
    - ETCD_NAME=etcd
    - ETCD_ADVERTISE_CLIENT_URLS=http://0.0.0.0:2379
    - ETCD_LISTEN_CLIENT_URLS=http://0.0.0.0:2379
    - ETCDCTL_API=3
    - ETCD_LOGGER=zap
    - ETCD_DATA_DIR=/etcd-data
    volumes:
    - "/etcd-data:/etcd-data"
    - "/etc/localtime:/etc/localtime:ro
```
