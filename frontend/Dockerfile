FROM node:18 AS nodejs

WORKDIR /app

#download all dependencies
COPY package.json package-lock.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx

COPY --from=nodejs /app/build  /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
