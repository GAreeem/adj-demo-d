# ---------- STAGE 1: build ----------
FROM node:20 AS build

WORKDIR /app

# Archivos de dependencias
COPY package*.json ./

RUN npm install

# Copia el código fuente
COPY . .

# 🔹 Variables para Vite (se leen en npm run build)
ARG VITE_API_HOST
ARG VITE_API_PORT
ARG VITE_API_BASE
ARG API_PROTOCOL


ENV VITE_API_HOST=${VITE_API_HOST}
ENV VITE_API_PORT=${VITE_API_PORT}
ENV VITE_API_BASE=${VITE_API_BASE}
ENV VITE_API_PROTOCOL=${API_PROTOCOL}

# Genera /dist usando las vars de arriba
RUN npm run build


# ---------- STAGE 2: nginx ----------
FROM nginx:alpine

# Copia el build estático
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
