## Commands

```bash
docker-compose up -d --build (build and run)
docker-compose down (stop and remove)
docker-compose stop <container>
docker-compose rm (remove)
docker-compose ps -a (all)
docker-compose logs --tail 100 <container>

docker-compose exec <container> <command>qq
```

## Redes

comandos para redes:
```bash
docker network ls (lista todas as redes)
docker network create <network-name> (cria uma rede)
docker network rm <network-name> (remove uma rede)
docker network inspect <network-name> (mostra as configurações da rede)
docker inspect <container-name> | grep IPAddress (pega o IP do container)
docker network prune (remove todas as redes não utilizadas)
```

### Bridge
- é o padrão
- o nome do container é acessivel a outros containers na mesma rede
- é uma rede interna, não é acessivel externamente

### Host
- muito performatica
- compartilha a rede do host

### Overlay
- é uma rede distribuida entre múltiplos Docker Daemon
- é uma rede sobreposta as redes específicas do host
- é muito útil para trabalhar com Docker Swarm
- é uma rede distribuida entre os nós do cluster

host.docker.internal é o IP do host da máquina