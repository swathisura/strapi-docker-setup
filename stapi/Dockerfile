FROM node:20-alpine

WORKDIR /app

RUN npm install -g npm@latest

RUN npx create-strapi-app@latest myapp --quickstart --no-run

WORKDIR /app/myapp

EXPOSE 1337

CMD ["npm", "run", "develop"]
