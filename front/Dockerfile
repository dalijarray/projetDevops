# Étape 1 : Construire l'application Angular
FROM node:20 as build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --prod

# Étape 2 : Servir avec NGINX
FROM nginx:1.21 AS production-stage
COPY --from=build /app/dist/front/browser /usr/share/nginx/html
EXPOSE 80
