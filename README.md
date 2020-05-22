Role Name
=========

Deploying Docker on CentOS7

After installing docker on fleet:

```sh
$ docker swarm init --advertise-addr [main IP]
```

Make a registry if using a local one:

```sh
$ docker service create --name registry --publish published=5000,target=5000 registry:2
```

Add the visualizer:
```sh
docker service create \
  --name=viz \
  --publish=8080:8080/tcp \
  --constraint=node.role==manager \
  --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock \
  dockersamples/visualizer
```

Requirements
------------

* CentOS7

Role Variables
--------------

registry_ip: Set this to the IP of the main docker server

License
-------

GPLv3
