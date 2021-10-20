# MONGODB
# Criando o Volume para persistir os dados do banco MongoDB
$ docker volume create mongo_vol

# Criando o container do MongoDb
$ docker container run -d \
-e MONGO_INITDB_ROOT_USERNAME=mongouser \
-e MONGO_INITDB_ROOT_PASSWORD=mongopwd \
-v mongo_vol:/data/db \
-p 27017:27017 \
--name mongodb \
mongo:4.4.3

#
# MARIADB
# Criando volume para persistir os dados do banco MariaDB
$ docker volume create mariadb_vol

# Criando o container MariaDB
$ docker container run -d \
-p 3306:3306 \
--name mariadb \
-v mariadb_vol:/var/lib/mysql \
-e MARIADB_ROOT_PASSWORD=mariadbpwd mariadb

#
# POSTGRESQL
# Criando o volume para persistir os dados do banco PostgreSQL
$ docker volume create postgre_vol

# Crinado o conatiner PostgreSQL
$ docker run  -d \
--name postgresql \
-p 5432:5432 \
-v postgre_vol:/var/lib/postgresql/data \
-e POSTGRES_PASSWORD=postgrepwd \
-e POSTGRES_USER=postgreuser postgres

#
# REDIS
# Criando o volume para persistir os dados do Redis
$ docker volume create redis_vol

# Criando o container Redis
$ docker run -d \
--name redisdb \
-p 6379:6379 \
-v redis_vol:/data \
redis redis-server --save 60 1 --loglevel warning

