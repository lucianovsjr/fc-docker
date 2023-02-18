`docker run -it ubuntu bash`
-i modo interativo. Mantém o stdin ativo para conseguir interagir com o container. Mantém o bash attached com o terminal.
-t tty. Permite digitar no terminal.

Obs: Roda a imagem, baixa e executa o comando bash.

As versões são tagueadas.

`docker run -it --rm ubuntu bash` remove o container.
Utilizado quando é necessário executar o processo mas não é necessário deixa-ló.
