Iniciando os containers:
```bash
>> docker network
>> docker network prune
>> docker network ls

>> docker run -dit --name ubuntu1 bash
>> docker run -dit --name ubuntu2 bash
>> docker ps

>> docker network inspect bridge
[
    {
        "Name": "bridge",
        "Id": "3fb7e55cea09a9d9b81f0ff35e1a4e70842a23bbb8ee6058f2e6d926c77f1fc5",
        "Created": "2023-02-27T07:48:49.621258926-03:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16",
                    "Gateway": "172.17.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "5a9cf69367d92491c296fc6ba8cf16b5252c1f7a0351270c08564107d53a3236": {
                "Name": "ubuntu1",
                "EndpointID": "8e3fb5c78a981b72440ea8919d2f2eb081cef2a59aeebb799a9359a261547b5b",
                "MacAddress": "02:42:ac:11:00:02",
                "IPv4Address": "172.17.0.2/16",
                "IPv6Address": ""
            },
            "8fafd845e956ff17d6ce9e3970e19f78dcc581061eec89abe5a0aed5bd0a22ee": {
                "Name": "ubuntu2",
                "EndpointID": "751c5ec70f2e9440f7d137329a8be0675764b98062fc9d9b993dfa1ae951b585",
                "MacAddress": "02:42:ac:11:00:03",
                "IPv4Address": "172.17.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        },
        "Labels": {}
    }
]

>>  docker attach ubuntu1
>>  ip addr show
>>  ping 172.17.0.3
>>  ping ubuntu2
ping: bad address 'ubuntu2'
>> docker rm -f ubuntu1 ubuntu2

>> docker network create --driver bridge mynet
>> docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
3fb7e55cea09   bridge    bridge    local
0ad365d48b9f   host      host      local
cb8d3adb6da9   mynet     bridge    local
e9c3ef4f3ac8   none      null      local

>> docker run -dit --name ubuntu1 --network mynet bash
>> docker run -dit --name ubuntu2 --network mynet bash
>> docker exec -it ubuntu1 bash
>> ping ubuntu2
PING ubuntu2 (172.19.0.3): 56 data bytes
64 bytes from 172.19.0.3: seq=0 ttl=64 time=0.166 ms

>> docker run -dit --name ubuntu3 bash
>> docker exec -it ubuntu3 bash
>> ping ubuntu2
ping: bad address 'ubuntu2'
>> ping 172.19.0.3 #ubuntu2
PING 172.19.0.3 (172.19.0.3): 56 data bytes
^C
--- 172.19.0.3 ping statistics ---
10 packets transmitted, 0 packets received, 100% packet loss

>> docker network connect mynet ubuntu3
>> docker exec -it ubuntu3 bash
>> ping ubuntu2
PING ubuntu2 (172.19.0.3): 56 data bytes
64 bytes from 172.19.0.3: seq=0 ttl=64 time=0.260 ms

>> docker network inspect mynet
[
    {
        "Name": "mynet",
        "Id": "cb8d3adb6da9e8d539c874117ef5d96398b7a2112c34dd9479cc827f83a5dd4c",
        "Created": "2023-02-27T23:54:09.440803328-03:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "011b988191a6c2629280d98cb3fa8fd8ff1b72bfd2db874a131d68bf4714bf04": {
                "Name": "ubuntu3",
                "EndpointID": "864c03800c56ce58cea897d4d8f15be0154da6e8190f8dfbd3a300fac536b717",
                "MacAddress": "02:42:ac:13:00:04",
                "IPv4Address": "172.19.0.4/16",
                "IPv6Address": ""
            },
            "6ef7a4e50a0eb57a324f51f3f8374711b671b9ed9b5bbada179294402c95a83d": {
                "Name": "ubuntu2",
                "EndpointID": "2dbda0f1a6d4dd439a3b603ccab99b8cc7f824e1268256e92c37708072ceca05",
                "MacAddress": "02:42:ac:13:00:03",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            },
            "763ea7ea83b41938dfed1694965153493ca88fd0c9891623721f7db7134f772d": {
                "Name": "ubuntu1",
                "EndpointID": "44f7742a4ce8760f098ebbdd07c97bbedc9a19011eff9dcbe3f2385bec821a09",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
```
Obs:
Quando os containers estão dentro da mesma network é possível utilizar o nome do container como address.
Na bridge padrão isso não funciona.
