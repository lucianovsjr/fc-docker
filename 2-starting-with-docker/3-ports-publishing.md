`docker run nginx`
Cria um container e segura no terminal a execução.

A porta do container não é a mesma do host.
O host não está mesma rede dos containers do docker.

`-p` publica a porta
Apontamento/redirecionamento de porta nos permite acessar aquela porta do
container através da porta do host que está executando a CLI.

`docker run -p 8080:80 nginx`
8080 da minha máquina para a 80 do nginx.

`docker run -d -p 8080:80 nginx`
`-d` detached, libera o terminal da execução do container.
