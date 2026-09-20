FROM node:22-alpine AS builder

WORKDIR /app

COPY main/package*.json ./

RUN npm ci

COPY main/ ./

RUN npm run build

FROM dockerhub.timeweb.cloud/library/nginx:mainline-alpine

COPY --from=builder /app/dist /usr/share/nginx/html

COPY ./server-config/nginx/frontend.nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80