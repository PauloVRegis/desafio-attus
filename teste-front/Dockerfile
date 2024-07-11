FROM node:14

WORKDIR /app

COPY package*.json ./

RUN npm install

RUN npm install -g @vue/cli

ENV PATH /app/node_modules/.bin:$PATH

COPY . .

RUN chmod -R 755 /app

RUN npm run build

FROM nginx:alpine

COPY --from=0 /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
