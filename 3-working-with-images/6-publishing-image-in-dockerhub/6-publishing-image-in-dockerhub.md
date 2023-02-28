Criar imagem
`docker build -t lucianovsjr/fc-nginx .`


## Subir imagem

A imagem precisa ter o username.

```
docker login
docker push lucianovsjr/fc-nginx
docker logout
docker rmi lucianovsjr/fc-nginx
docker run --rm -d -p 8080:80 lucianovsjr/fc-nginx
```
Irá baixar a imagem e criar o container.

## Observações
Se a imagem não for utilizado durante um determinado tempo ela será inutilizada.
É bom devez enquando fazer um pull para manter ela ativa.
