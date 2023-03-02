É necessário ter o jogo de cintura para subir qualquer coisa que seja necessário.

## Passo a passo para criar um Dockerfile
1. Ir no Docker Hub e escolher uma imagem e versão base.
2. Criar um container e ir executando os comandos com o intuito de ir copiando para o Dockerfile a "receita de bolo"
3. Criar o container `docker run -it --name php php:8.1.16-cli bash`
4. Organizar o run do dockerfile em contextos, visando reaproveitar as layers.
5. Criar a imagem para testar: `docker build -t lucianovsjr/fc-php laravel/`
6. Criar container da imagem: `docker run --rm --name example-php -p 8000:8000 lucianovsjr/fc-php`
7. Ver logs: `docker logs example-php`
8. Substituir o command: `docker run --rm --name example-php -p 8000:8000 lucianovsjr/fc-php --host=0.0.0.0 --port=8001`
9. Subir: `docker push lucianovsjr/fc-php`
