Propriedade `command` é o `CMD` do dockerfile, comando que vem após o entrypoint.

`restart: always`, se por algum motivo o container cair irá fazer o restart sozinho.

`tty: true`, para conseguirmos interagir com o container.

Propriedade `volumes` faz a criação e mapeamento dos volumes utilizados no container.

Para setar variáveis de ambiente utilizando docker run: `docker run -e VAR2=value2`.

Propriedade `environment` define as variáveis de ambiente no container.
