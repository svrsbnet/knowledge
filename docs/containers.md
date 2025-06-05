# Commandos comunes

## Arrancar contenedor

    docker run --help

Opcions comunes:

    -d: Arranca el contenedor en segundo plano.
    -p: Mapea un puerto del contenedor al puerto del host.
    -v: Mapea un volumen del host al contenedor.
    --name: Asigna un nombre al contenedor.
    --rm: Elimina el contenedor al pararlo.
    -e: Define una variable de entorno.
    --env-file: Define un archivo de variables de entorno.
    --restart: Define la política de reinicio

Ejemplos:

    docker run -it -d ubuntu
    docker run -d ubuntu --name <container_name>

## Consultar estado de los contenedores

    docker ps --help

Ejemplos:

    docker ps
    docker ps -a

## Ver la salida del contenedor

    docker logs --help

Ejemplos:

    docker logs -f <container_id>
    docker logs -f <container_id>

## Ver salida a tiempo real

    docker attach --help

## Conectar a un contenedor

    docker exec --help  # (docker exec -it) 

## Iniciar un contenedor

    docker start --help

## Reiniciar un contenedor

    docker retsart --help

## Parar un contenedor

    docker stop --help

## Eliminar contemedor

    docker rm --help

## Eliminar todos los contenedores parados

    docker container prune

docker image list

docker images list
