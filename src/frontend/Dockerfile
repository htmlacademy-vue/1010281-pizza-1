FROM node:16-slim

WORKDIR /frontend

COPY package.json package-lock.json ./

RUN apt update

RUN apt install build-essential -y

RUN apt install python3 -y

RUN npm install --legacy-peer-deps

RUN npm install @vue/cli@4.5.8 -g --legacy-peer-deps

COPY . .

CMD ["npm", "run", "serve"]
