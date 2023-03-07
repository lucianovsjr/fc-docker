## Nginx como proxy reverso
No nginx temos os arquivos .conf na qual iremos configuras os domínios.

`mkdir /var/www/html -p`
-p: Criar diretorio e sub-diretorios caso não exista

Gerar imagem do nginx: `docker build -t lucianovsjr/fc-nginx:prod nginx/ -f nginx/Dockerfile.prod`

Criar network: `docker network create laranet`
Por padrão utiliza o driver bridge caso o parâmetro --driver não seja definido.

Criar container do laravel: `docker run -d --network laranet --name laravel lucianovsjr/fc-php:prod`

Quem está na network laranet consegue acessar o container laravel pela porta 9000.

Criar container do nginx:`docker run -d --network laranet --name nginx -p 8080:80 lucianovsjr/fc-nginx:prod`

Ver logs: `docker logs nginx`

Criar link simbolico: `ln -s public html`
Sempre que acessa a pasta html irá acessar a pasta public.
Pasta html aponta para a pasta public.

Remover containers: `docker rm -f laravel nginx`
