# Imagen base
FROM node:20

WORKDIR /app

# Copiar package.json primero para cachear dependencias
COPY package*.json ./

RUN npm install -g @angular/cli && npm install

# Copiar todo el código
COPY . .

# Exponer el puerto de Angular dev server
EXPOSE 4200

# Comando para desarrollo
CMD ["ng", "serve", "--host", "0.0.0.0", "--poll", "2000"]
