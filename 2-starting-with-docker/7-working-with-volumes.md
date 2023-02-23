bind mount: Monta uma pasta do computador para o container

## volume
É um conceito especifico no Docker, por conseguirmos gerenciar.
Utilizado quando é necessário persistir dados do container no computador.

É possível criar um volumes e mapear esse volume em diversos containers.

Criar um volume `docker volume create myvolume`.

Inspecionar um volume `docker volume inspect myvolume`.
```json
[
    {
        "CreatedAt": "2023-02-22T22:43:24-03:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/myvolume/_data",
        "Name": "myvolume",
        "Options": null,
        "Scope": "local"
    }
]
```
Mountpoint: Caminho do volume na máquina.

### Mapear um volume no container
```bash
docker run -d --name fc-nginx1 --mount type=volume,source=myvolume,target=/app nginx
docker exec -it fc-nginx1 bash
cd /app
touch hello

docker run -d --name fc-nginx2 --mount type=volume,source=myvolume,target=/app nginx
docker exec -it fc-nginx2 bash
cd /app
ls

docker run -d --name fc-nginx3 -v myvolume:/app nginx
docker exec -it fc-nginx3 bash
cd /app
ls
```
O arquivo hello estará presente nos containers.

### Super dica
`docker volume prune`
Limpa os volumes que não está sendo utilizados.
