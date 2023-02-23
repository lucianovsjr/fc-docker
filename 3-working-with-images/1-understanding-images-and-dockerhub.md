As imagens utilizadas pelo Docker ficam no docker hub.
Todas as imagens ficam armazenadas nele.

Docker hub é o container registry do Docker.

É comum fazer o push de 2 imagens, uma da versão fixa e outra da latest.

`docker pull`
Comando para baixar uma imagem.

Empresas como amazon e google possuem o próprio container registry.

`docker images`
Lista as imagens já baixadas

`docker pull php`
Baixa php:latest
Baixa as layers que não existem no computador.

`docker rmi php:latest`
Remove a imagem do php.
Remove todos os layers.
