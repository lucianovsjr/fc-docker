## Como ver o Dockerfile de uma imagem?

No Docker Hub é possível acessar o link do Dockerfile no Github.
Ex.: https://hub.docker.com/_/nginx

Um container pode acessar outro através da porta que é exposta.

Entrypoint:
```
docker run --rm -it nginx bash
cat docker-entrypoint.sh
```
A última linha possui `exec "$@"`, esse comando executa o que vem depois da chamada do arquivo.
Ex: `./docker-entrypoint.sh echo "hello"`

## Outros

É possível declarar variaveis de ambiente no Dockerfile com o comando `ENV`.
Ex.: `ENV NGINX_VERSION 1.23.3`
