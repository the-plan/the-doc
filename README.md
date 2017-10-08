# the-doc
> How to run the demonstration

1. run Redis: `redis-server`
2. start basestars:
```
COLOR=FF5733 REDIS_RECORDS_KEY="bsg-the-plan" SERVICE_NAME="BaseStar01" PORT=8081 SERVICE_PORT=8081 java  -jar target/basestar-1.0-SNAPSHOT-fat.jar&
COLOR=339FFF REDIS_RECORDS_KEY="bsg-the-plan" SERVICE_NAME="BaseStar02" PORT=8082 SERVICE_PORT=8082 java  -jar target/basestar-1.0-SNAPSHOT-fat.jar&
COLOR=46FF33 REDIS_RECORDS_KEY="bsg-the-plan" SERVICE_NAME="BaseStar03" PORT=8083 SERVICE_PORT=8083 java  -jar target/basestar-1.0-SNAPSHOT-fat.jar&
COLOR=FF33F0 REDIS_RECORDS_KEY="bsg-the-plan" SERVICE_NAME="BaseStar04" PORT=8084 SERVICE_PORT=8084 java  -jar target/basestar-1.0-SNAPSHOT-fat.jar&
```
3. run "bsg-monitor": `REDIS_RECORDS_KEY="bsg-the-plan" PORT=8080 SERVICE_PORT=8080 sbt run`
4. run "bsg-map": `PORT=7070 RAIDERS_SERVICE=http://localhost:8080/api/raiders npm start`
5. start raiders (kotlin version):
```
startPort=9090

for i in `seq 1 10`;
do
    resultat=$(($startPort+$i))
    REDIS_RECORDS_KEY="bsg-the-plan" SERVICE_NAME="R" SERVICE_PORT=$resultat PORT=$resultat java  -jar target/k-raider-1.0-SNAPSHOT-fat.jar&
done
```
6. start raiders (groovy version):
```
startPort=9090

for i in `seq 21 26`;
do
    resultat=$(($startPort+$i))
    REDIS_RECORDS_KEY="bsg-the-plan" SERVICE_NAME="R" SERVICE_PORT=$resultat PORT=$resultat java  -jar target/g-raider-1.0-SNAPSHOT-fat.jar&
done
```
7. fake raider (run the nodejs raider): 
```
cd fake-raider
node index.js
```

## Play

- use `jcmd` command to list all java process
- try to kill some basestars
- try to kill all basestars, then re start some basestars



