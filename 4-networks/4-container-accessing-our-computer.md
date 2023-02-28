## Como acesso o Docker host pelo container?

```bash
>> php -S 0.0.0.0:8000
>> curl http://localhost:8000

>> docker run --rm -it --name ubuntu ubuntu bash
>> apt-get update
>> apt-get install curl -y
>> curl http://host.docker.internal:8000
```
