FROM node:14

WORKDIR /app

COPY package*.json ./

RUN npm install --force

RUN npm i @vue/cli-service

COPY . .

RUN chmod -R 755 /app

RUN npm run build

FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

