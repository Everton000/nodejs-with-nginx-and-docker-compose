FROM node:15

ADD https://github.com/jwilder/dockerize/releases/download/v0.6.1/dockerize-linux-amd64-v0.6.1.tar.gz /usr/local/bin/
RUN tar -C /usr/local/bin -xzvf /usr/local/bin/dockerize-linux-amd64-v0.6.1.tar.gz

WORKDIR /app

COPY package*.json ./
RUN npm install --production
COPY . .

EXPOSE 3000

CMD dockerize -wait tcp://db:3306 -timeout 20s && node index.js
