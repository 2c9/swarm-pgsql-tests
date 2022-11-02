
## Init a swarm cluster
```bash
docker swarm init --advertise-addr <ipaddr>
docker swarm join-token manager
```

## Add other nodes
```bash
docker swarm join --token ... <ipaddr>:2377
docker swarm join --token ... <ipaddr>:2377
docker node ls
```

## Create volumes for containers and fix permissions
```
mkdir /srv/etcd{1,2,3}-data
mkdir /srv/pg{1,2,3}
chown -R 999:999 /srv/pg{1,2,3}
chmod -R 700 /srv/pg{1,2,3}
```

## Deploy the stack
```bash
docker stack deploy -c docker-compose.yaml pgsql
```