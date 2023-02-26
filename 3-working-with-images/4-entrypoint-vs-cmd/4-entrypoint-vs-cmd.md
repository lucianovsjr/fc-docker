`CMD` é um comando variável.
Tudo que for colocado após a imagem na criação de um container irá substiuir o CMD.
Ex: `docker run --rm lucianovsjr/fc-docker-hello echo "oi"`

`ENTRYPOINT` é um comando fixo a ser executado.

`CMD` é utilizado como parâmetros para o `ENTRYPOINT` ou como comando a ser executado (substituível).
Ex: `docker run --rm lucianovsjr/fc-docker-hello "teste"`

Existem casos que é necessário somente o `CMD`, outros somente o `ENTRYPOINT`, e outros ambos.

## Dica

`docker ps -a -q`
Lista os ids dos containers ativos e inativos.

`docker rm $(docker ps -a -q) -f`
Remove todos os containers.
