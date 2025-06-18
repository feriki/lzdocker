### What is lzdocker?
A tool that generates the docker run command for running Docker containers with just one click.


## Usage
X86 or AMD architecture uses `lzdocker`, ARM architecture uses `lzdocker-arm`

# Excute command
-> For all runing containers</br>
lzdocker {allrun}

-> For all containers include shutdown</br>
lzdocker {all}

> For one or more containers</br>
lzdocker <CONTAINER NAME or ID> [CONTAINER...]

# Example:
-> input:</br>
./lzdocker milvus-etcd

-> output:</br>
docker run -d \
 --name milvus-etcd \
 --privileged  \
 --cpus 4.0 \
 --env ETCD_ELECTION_TIMEOUT=5000 \
 --health-interval 30s \
 --health-retries 3 \
 --health-timeout 20s \
 --label com.docker.compose.container-number=1 \
 --label com.docker.compose.depends_on="" \
 --label com.docker.compose.oneoff=False \
 --label com.docker.compose.project=docker \
 --label com.docker.compose.project.working_dir=/opt/milvus/docker \
 --label com.docker.compose.service=etcd \
 --label com.docker.compose.version=2.20.2 \
 -m 2GB \
 --restart=always \
 -v /opt/milvus/docker/volumes/etcd:/etcd:rw \
 -v /opt/milvus/docker/logs/etcd:/tmp:rw \
 quay.io/coreos/etcd:v3.5.5 etcd -advertise-client-urls=http://127.0.0.1:2379 -listen-client-urls http://0.0.0.0:2379 --data-dir /etcd --log-outputs stdout,/tmp/info.log


