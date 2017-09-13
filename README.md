# docker-gluster-volume-plugin

docker volume plugin for glusterfs

### Build

```sh
glide install
go build
```

### Usage

Start volume plugin

- `server` :  gluster node name(only use one node)
- `etcd` : etcd server address. when plugin running in multi-host environment, it must required, because plugin use etcd to sync docker volume config between hosts

```sh
docker-gluster-volume-plugin -server server51 -etcd http://<ip>:<port>
```

Create volume, the `vname`is your gluster volume name

```
docker volume create --driver glusterfs --opt vname="gv5" --name d-gv5
```

Run container

```sh
docker run --name test -v d-gv5:/data -td ubuntu:14.04.3
```

## Reference

https://github.com/sapk/docker-volume-gluster

https://github.com/calavera/docker-volume-glusterfs
