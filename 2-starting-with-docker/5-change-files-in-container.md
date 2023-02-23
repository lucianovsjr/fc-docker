`run -d --name fc-nginx nginx`
--name definir nome do container

Criar container da aula: `docker run -d --name fc-nginx -p 8080:80 nginx`

`docker exec`
Executa um comando no container

`docker exec fc-nginx ls`
Executa o comando ls no container

`docker exec -it fc-nginx bash`
Executa o bash e prende no terminal

Alterar index.html padrão do nginx:
```bash
cd /usr/share/nginx/html
apt-get update
apt-get install vim
vim index.html
```

Para manter as imagens mais leves, o cache de imagens do apt-get é limpo.

Se o container for removido, por padrão as alterações realizadas serão perdidas.
