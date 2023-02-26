## Comandos bastante utilizados no Dockerfile

`workerdir`:
Diretório de trabalho do container.
Cria uma pasta dentro do container e te coloca lá dentro por padrão.

`&&`:
Executa mais de um comando na mesma linha.

`\`:
Quebra de linha.

`copy`:
Copia um arquivo ou arquivos de uma pasta do pc para o container.

## Observações

As layers são reaproveitadas quando estão no chace.
Cada linha do Dockerfile gera uma layer.
Se outro Dockerfile utiliza a mesma imagem base e em seguida o mesmo comando, a layer será reaproveitada.

Por padrão é utilizado o usuário root, é possivel utilizar outro usuário com o comando `USER` mas esse usuário deve existir no passwd.
