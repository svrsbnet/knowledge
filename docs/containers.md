# About Containers

- [Common contaiers commands](README.md#common-contaiers-commands)
- [Common images commands](README.md#common-images-commands)

## Common contaiers commands

### Run container

    docker run --help

Common options

    -d:             # Arranca el contenedor en segundo plano.
    -p:             # Mapea un puerto del contenedor al puerto del host.
    -v:             # Mapea un volumen del host al contenedor.
    --name:         # Asigna un nombre al contenedor.
    --rm:           # Elimina el contenedor al pararlo.
    -e:             # Define una variable de entorno.
    --env-file:     # Define un archivo de variables de entorno.
    --restart:      # Define la política de reinicio

Examples

    docker run -it -d ubuntu
    docker run -d ubuntu --name <container_name>

### Check conatiners status

    docker ps --help

Examples

    docker ps
    docker ps -a

### Check logs containers

    docker logs --help

Examples

    docker logs -f <container_id>
    docker logs -f <container_id>

### Atach to conatiners

    docker attach --help

### Run remote commands

    docker exec --help

Examples

    docker exec f5783de3f3b3 df -H

### Conectar a un contenedor

    docker exec --help 

Examples

    docker exec -it

### Start containers

    docker start --help

### Restart containers

    docker retsart --help

### Stop containers

    docker stop --help

### Delete containers

    docker rm --help

### Delete all stopped containers

    docker container prune

---

## Common images commands

blablabla
