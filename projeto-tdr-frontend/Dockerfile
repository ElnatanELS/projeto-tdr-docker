FROM node:alpine as angular

WORKDIR /app

COPY package*.json ./

RUN npm install --silent

COPY . .

RUN npm run build

FROM nginx:alpine
VOLUME /var/cache/nginx

COPY --from=angular app/dist/projeto-tdr-frontend /usr/share/nginx/html
COPY ./config/nginx.conf /etc/nginx/conf.d/default.conf

