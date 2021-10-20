# CRIANDO CONTAINERS DE FERRAMENTAS ADMINISTRATIVAS WEB E OS BANCOS

# MONGODB
###### - Criando o Volume para persistir os dados do banco MongoDB
$ docker volume create mongo_vol

###### - Criando a rede para o MondoDB
$ docker network create mongodb_net

###### - Criando o container do MongoDb
$ docker container run -d \
-e MONGO_INITDB_ROOT_USERNAME=mongouser \
-e MONGO_INITDB_ROOT_PASSWORD=mongopwd \
-v mongo_vol:/data/db \
-p 27017:27017 \
--network mongodb_net \
--name mongodb \
mongo:4.4.3

###### - Criando o MONGO-EXPRESS - Ferramenta web para administrar o MongoDB
$ docker run -d --name mongo_express --network mongodb_net -p 8081:8081 -e ME_CONFIG_MONGODB_URL="mongodb://mongouser:mongopwd@mongodb:27017/admin"  mongo-express

#
# MARIADB
###### - Criando volume para persistir os dados do banco MariaDB
$ docker volume create mariadb_vol

###### - Criando a rede para o MariaDB
$ docker network create mariadb_net

###### - Criando o container MariaDB
$ docker container run -d \
-p 3306:3306 \
--name mariadb \
--network mariadb_net \
-v mariadb_vol:/var/lib/mysql \
-e MARIADB_ROOT_PASSWORD=mariadbpwd mariadb

###### - Criando PHPMYADMIN - Ferramenta web para administrar o MariaDB
$ docker container run --name phpmyadmin -p 8080:80 --network mariadb_net -e PMA_HOST=mariadb phpmyadmin

# POSTGRESQL
###### - Criando o volume para persistir os dados do banco PostgreSQL
$ docker volume create postgre_vol

###### - Criando a rede para o PostgreSQL
$ docker network create postgre_net

###### - Crinado o conatiner PostgreSQL
$ docker run  -d \
--name postgresql \
-p 5432:5432 \
--network postgre_net \
-v postgre_vol:/var/lib/postgresql/data \
-e POSTGRES_PASSWORD=postgrepwd \
-e POSTGRES_USER=postgreuser \
 postgres

###### - Criando PGADMIND - Ferramenta we para administrar o PostgreSQL
$ docker run -d --name pgadmin4 --network postgre_net -p 5050:5050 fenglc/pgadmin4

- Dados de acesso

    Host: <ip da sua máquina:5050> \
    Usarname: pgadmin4@pgadmin.org \
    Password: admin


#
# REDIS
$ docker run -d --name redis-commander --env REDIS_HOSTS=redisdb --network redis_net -p 8081:8081 rediscommander/redis-commander:latest
