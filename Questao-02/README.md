# MONGO-EXPRESS
$ docker run -d --name mongo_express -p 8081:8081 --network mongodb_net -e ME_CONFIG_MONGODB_URL="mongodb://mongouser:mongopwd@mongodb:27017/admin"  mongo-express

#
# MARIADB
$ docker container run --name phpmyadmin -p 8080:80 --network mariadb_net -e PMA_HOST=mariadb phpmyadmin

#
# POSTGRESQL
$ docker run -d --name pgadmin4 --network postgre_net -p 5050:5050 fenglc/pgadmin4

#
# REDIS
$ docker run -d --name redis-commander --env REDIS_HOSTS=redisdb --network redis_net -p 8081:8081 rediscommander/redis-commander:latest
