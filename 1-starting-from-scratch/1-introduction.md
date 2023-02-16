## O que são containers?
Resposta genérica:
Um container é um padrão de unidade de software que empacota código e todas as
dependências de uma aplicação fazendo que a mesma seja executada rapidamente de
forma confiável de um ambiente computacional para o outro.

## Como funciona os Containers?
Um SO possui processos que ficam executando.

Namespaces: isola os processos

Um conjunto de processo fica em um namespace.
Processos filhos ficam dentro de um processo pai (principal).

Se o processo pai for removido o container é destruido.

O container pensa que tudo que está sendo executado nesse processo pai é o SO.

O processos do container não enxergam os processos do SO.

sub-processos do processo principal: Pid, User, Network, File system.

Cgroups: Controla os recursos computacionais do container.
Separa uma parte da memória e cpu do SO para o container.

Container isola os processos.

File System: OFS (Overlay File System)
Possui dependências que são layers.
A diferença é copiada para uma nova imagem.
Uma imagem possui várias layers de dependências.

Container roda em cima do SO, aproveita todo o kernel do SO, as libs, etc.
Ele não contém todo o SO, apenas os pedaços que ele precisa para rodar.

## Imagens
Em docker, não é um snapshot, são camadas.

Scratch (imagem vazia)
    -> Ubuntu (Pegar somente a parte que o SO não tem)
        -> bash
        -> ssh.d
            -> MyApp:v1

As imagens trabalham com dependências.
Árvore de dependências.
As imagens são reaproveitadas em outras imagens que a usam de dependência.

As imagens possuem nome e versão.

## Dockerfile
Uma forma de criar imagens.
Dockerfile: Arquivo declarativo onde é descrito como será a imagem que irá sofrer o build.

```bash
FROM: ImageName
RUN: Comandos ex: apt-get install xx
EXPOSE: 8000
```

## Como funciona os Containers? 2
Um processo terá uma imagem, o estado da imagem é imutável.
Container utiliza uma imagem para subir. Esse container já sobe rodando a imagem por isso é tão rápido.

Para criar um container o Docker sobe a imagem e cria uma layer "read/writer".
Essa camada "read/writer" permite fazer alterações no container.
Se matar o container os dados dessa camada são excluídos.

Apartir de um Dockerfile é criado uma imagem através do build.

É possível criar nova imagem apartir de um container baseada nas alterações realizadas na layer "read/writer" através do commit.

## Aonde ficam as imagens?
Ficam em um "image registry".
Como se fosse um repostório de imagens.

## Como funciona os Containers? 3

Quando você está utilizando uma imagem no Dockerfile por exemplo, essa imagem está vindo do "image registry".
```
FROM: ImageName
```

Ao gerar o build pode ser feito o push dessa nova imagem.

## Como o Docker funciona?

Docker Host: Onde o docker roda, processo fica rodando em background.
Disponibiliza uma api "daemon - API"

Docker Client: conversa com a API disponbilizada pela daemon do docker.
    Podemos criar container, rodar, etc.

Docker Host:
    Dentro dele possuimos:
        Daemon - API
        Cache: Armazena todas as imagens que já foram utilizadas (pull, push, build, etc)
        Volumes: Gerenciamento de volumes. Permite fazer a persistência dos dados. Resolve o problema de manter os dados após matar um container.
        Network: Garante a comunicação entre containers.
