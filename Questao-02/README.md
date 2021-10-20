# CRIANDO CONTAINERS DE FERRAMENTAS ADMINISTRATIVAS WEB E OS BANCOS

#
# MONGODB
## Criando o Volume para persistir os dados do banco MongoDB
$ docker volume create mongo_vol

## Criando a rede para o MondoDB
$ docker network create mongodb_net

## Criando o container do MongoDb
$ docker container run -d \
-e MONGO_INITDB_ROOT_USERNAME=mongouser \
-e MONGO_INITDB_ROOT_PASSWORD=mongopwd \
-v mongo_vol:/data/db \
-p 27017:27017 \
--network mongodb_net \
--name mongodb \
mongo:4.4.3

## MONGO-EXPRESS - Ferramenta web para administrar o mongodb
$ docker run -d --name mongo_express -p 8081:8081 -e ME_CONFIG_MONGODB_URL="mongodb://mongouser:mongopwd@mongodb:27017/admin"  mongo-express

#
# MARIADB
$ docker container run --name phpmyadmin -p 8080:80 --network mariadb_net -e PMA_HOST=mariadb phpmyadmin

#
# POSTGRESQL
$ docker run -d --name pgadmin4 --network postgre_net -p 5050:5050 fenglc/pgadmin4

#
# REDIS
$ docker run -d --name redis-commander --env REDIS_HOSTS=redisdb --network redis_net -p 8081:8081 rediscommander/redis-commander:latest
