# MONGO-EXPRESS
$ docker run -it --rm -p 8081:8081 --network mongodb_net -e ME_CONFIG_MONGODB_URL="mongodb://mongouser:mongopwd@mongodb:27017/admin"  mongo-express

#
# MARIADB
$ docker container run --name phpmyadmin --rm -p 8080:80 --network mariadb_net -e PMA_HOST=mariadb phpmyadmin

#
# POSTGRESQL
$ docker run --rm --name pgadmin4-desafio --network postgre_net -p 5050:5050 fenglc/pgadmin4

#
# REDIS
$ docker run --rm --name redis-commander --env REDIS_HOSTS=redisdb --network redis_net -p 8081:8081 rediscommander/redis-commander:latest
