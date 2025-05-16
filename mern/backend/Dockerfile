FROM node:18.9.1

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 5050

CMD ["npm", "start"]
# This Dockerfile is for a Node.js application. It uses the official Node.js image as the base image.