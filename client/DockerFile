# Fase 1: construir los recursos con Node
FROM node:20 AS build

WORKDIR /app

COPY package.json ./
RUN npm install

COPY . .
RUN npm run build

# Fase 2: servir los archivos estáticos con Nginx
FROM nginx:alpine

# Copiamos los archivos generados al directorio correcto
COPY --from=build /app/dist /usr/share/nginx/html

# Exponemos el puerto 80
EXPOSE 80

# Ejecutamos nginx en primer plano
CMD ["nginx", "-g", "daemon off;"]
