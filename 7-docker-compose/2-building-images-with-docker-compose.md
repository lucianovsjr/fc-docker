Muitas vezes no dia a dia não iremos trabalhar com imagens fechadas (prontos para produção).
Normalmente iremos trabalhar com imagens que nos ajudem no dia a dia.

Deixando o `image` o docker-compose sempre irá gerar/utilizar a imagem com o nome especificado.

Fluxo do build da imagem:
1. Sempre que subir o docker-compose `docker-compose up`
2. O docker-compose irá olhar a propriedade `build`
3. Irá gerar a imagem olhanda para a pasta da propriedade `context` com o nome do arquivo da propriedade `dockerfile`
4. Essa imagem terá o nome da propriedade `image`, se não tiver definido, o docker irá gerar com um nome interno

```bash
# Subir o docker-compose sem travar o terminal
>> docker-compose up -d
Creating network "7dockercompose_laranet" with driver "bridge"
Creating laravel ... 
Creating nginx ... 
Creating laravel
Creating laravel ... done

>> docker-compose ps   
 Name                Command              State                  Ports                
--------------------------------------------------------------------------------------
laravel   docker-php-entrypoint php-fpm   Up      9000/tcp                            
nginx     nginx -g daemon off;            Up      0.0.0.0:8080->80/tcp,:::8080->80/tcp

>> docker-compose down
Stopping nginx   ... done
Stopping laravel ... done
Removing nginx   ... done
Removing laravel ... done
Removing network 7dockercompose_laranet

# --build: Utilizar sempre que houver alteração no Dockerfile
# Gera as imagens novamente
>> docker-compose up -d --build
```

A imagem não é criada toda vez que o docker-compose é iniciado.
