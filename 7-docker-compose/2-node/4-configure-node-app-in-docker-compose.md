```bash
>> docker-compose up -d                           
Creating network "2node_node-network" with driver "bridge"
Creating db ... 
Creating app ... 
Creating app
Creating app ... done

>> docker exec -it app bash
>> root@1e5b6aa96709:/usr/src/app# ls
Dockerfile  Dockerfile.prod  index.js  package-lock.json  package.json
>> root@3b3ee198db55:/usr/src/app# npm install

added 57 packages, and audited 58 packages in 1s

7 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
npm notice 
npm notice New major version of npm available! 7.7.6 -> 9.6.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v9.6.0
npm notice Run npm install -g npm@9.6.0 to update!
npm notice 
>> root@3b3ee198db55:/usr/src/app# node index.js
Running on port 3000
```