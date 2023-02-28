## Introdução
Docker possui um mecanismo de network.
Uma rede interna dentro do Docker.

Um das suas finalidades é fazer a conexão entre containers.
Ex: 1 container com o Mysql e outro com o Laravel.

## Tipos de network
1. Bridge
Network padrão utilizada pelos containers.
Utilizada quando há necessidade de um container se conectar com outro.

2. Host
Mescla a network do Docker com a network do Docker client (Minha máquina).

3. Overlay
Vários dockers em máquinas diferentes e é necessário que eles se comuniquem como se estivessem na mesma rede.
Ex: docker swarm

4. Macvlan
Ex: Seta um mac-adress é um container, aparece como uma network que está plugado na rede.

5. None
Sem rede. Isolado.

Mais utilizado: Bridge e host.
