FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . ./

RUN npm run build

FROM dockerhub.timeweb.cloud/library/nginx:mainline-alpine

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80