FROM node:14.17.5
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE "8181:8181"
CMD [ "node", "server.js" ]