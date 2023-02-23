`docker run -d --name fc-nginx -p 8080:80 -v /home/lucianovsjr/www/study/full-cycle/fc-docker/2-starting-with-docker/html:/usr/share/nginx/html nginx`
-v montar um volume, montar o diretório da máquina no container. `-v "máquina":"container"`

Se o container for removido o volume é mantido na máquina.

O comando -v é um dos mais antigos do docker.
Atualmente o comando mais utilizado é p --mount

`docker run -d --name fc-nginx -p 8080:80 --mount type=bind,source="$(pwd)"/2-starting-with-docker/html,target=/usr/share/nginx/html nginx`
--mount
    type: Tipo de volume
    source: Origem, caminho da máquina local
    target: Destino, caminho do container

pwd = pega o caminho da pasta que você está

## Diferença entre -v --mount

`docker run -d --name fc-nginx -p 8080:80 -v "$(pwd)"/2-starting-with-docker/html/x:/usr/share/nginx/html nginx`
Pasta "x" não existe mas ela é criada ao criar o container.

`docker run -d --name fc-nginx -p 8080:80 --mount type=bind,source="$(pwd)"/2-starting-with-docker/html/x,target=/usr/share/nginx/html nginx`
Nesse caso irá ocorrer um error pois a pasta não existe, não sendo possível fazer o bind com uma pasta inexistente.
