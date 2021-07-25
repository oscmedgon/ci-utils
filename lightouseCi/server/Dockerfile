FROM node:lts

WORKDIR /usr/share/app

COPY ./package.json .
COPY ./package-lock.json .

RUN npm ci || npm i

COPY server.js .

CMD ["node", "server.js"]
