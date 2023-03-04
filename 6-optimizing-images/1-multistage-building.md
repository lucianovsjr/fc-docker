## Otimizar imagens

Em comum quando estivermos desenvolvendo utilizarmos uma imagem que possui muitos recursos.

Já em produção é recomendado ter uma imagem mais enxuta.
Será mais rápido para subir e baixar por conta do tamanho.
Também terá mais segurança por ter menos recurso assim dimunuindo as vunerabilidades.

É comum utilizar a imagem alpine do linux em produção, que é uma versão mais pequena mas que "da conta do recado".

## Multistage building
Consiste em fazer o build da imagem em mais de uma etapa.
Temos o stage inicial que gera uma imagem e outro que otimiza.

Criar o Dockerfile de produção. `/laravel/Dockerfile.prod`

`COPY --from=builder /var/www/laravel .`
Copia o conteudo da pasta "/var/www/laravel" do build "builder" para a pasta que está no momento.

Gerar uma imagem de produção: `docker build -t lucianovsjr/fc-php:prod laravel/ -f laravel/Dockerfile.prod`

Listar imagens: `docker images | grep php`
