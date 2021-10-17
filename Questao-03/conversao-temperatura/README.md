# Criando imagem do app conversao-temperatura

$ docker build -t israeldoamaral/conversao-temperatura:v1 .

$ docker container run -d -p 8080:8080 israeldoamaral/conversao-temperatura:v1
