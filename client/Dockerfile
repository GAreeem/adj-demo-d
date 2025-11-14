FROM node:20 AS build

WORKDIR /app

#package.log.json, package-lock.json -> /app
COPY package*.json ./

#funciona para generar EL NODE_MODULES
RUN npm install

#client/* -> /app/*
COPY . .

#funciona para generar la carpeta /dist
RUN npm run build

#etapa 2 construccion de la imagen
FROM nginx:alpine

#Servir todos los recursos generados en la  etapa anterior en la imagen
COPY --from=build /app/dist /usr/share/nginx/html


ARG API_HOST
ARG API_PORT
ARG API_BASE

ENV VITE_API_HOST=$API_HOST
ENV VITE_API_PORT=$API_PORT
ENV VITE_API_BASE=$API_BASE



EXPOSE 80