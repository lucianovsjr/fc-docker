Utilizar o container para não precisar ter o node instalado na máquina.
```bash
>> docker run --rm -it -v $(pwd)/node/:/usr/src/app -p 3000:3000 node:15 bash
>> cd /usr/src/app
>> touch hello
>> npm init
>> npm install express --save
>> touch index.js
>> node index.js
```
Criamos o Dockerfile baseado na aplicação acima.

Estamos desenvolvendo usando o container sem o node instalado na máquina.

Sempre que for gerar o build da aplicação deve ser copiado os arquivos para a imagem.
```bash
>> docker build -t lucianovsjr/fc-express node/
>> docker run --rm -p 3000:3000 lucianovsjr/fc-express
>> docker push lucianovsjr/fc-express
```

Dockerfile = Usado para desenvolver
Dockerfile.prod = Usado para publicar
`docker build -t lucianovsjr/fc-express node/ -f node/Dockerfile.prod`
