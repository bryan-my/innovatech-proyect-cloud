# Etapa 1: Compilación (Build) - Queda igual
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build 

# Etapa 2: Producción (Cambiamos a la imagen estándar de Nginx que sí usa el puerto 80)
FROM nginx:alpine

# Copiamos los archivos compilados desde la etapa 1
COPY --from=builder /app/dist /usr/share/nginx/html

# Ahora sí exponemos el puerto 80
EXPOSE 80
