`docker ps` container ativos (rodando) na máquina.

Criando o primeiro container:
`docker run hello-world`

"latest" é a tag da última versão.
Se não especificar a tag irá utilizar a "latest".

Com o comando `docker run` se a imagem não exister localmente irá baixar.

Após baixar essa imagem o `entrypoint` ou `command` da imagem é executado.
Um processo é executado, se o `entrypoint` ou `command` da imagem não segurar o processo, o processo será executado e depois morrerá.

container é um processo.

`docker ps -a` exibe todos os containers que estão na máquina ativos ou inatavios.

Se não especificar o nome do container ao cria-ló, será gerado um nome aleatório.
