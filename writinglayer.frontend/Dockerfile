# Trin 1: Build stage
FROM node:20-alpine AS build
WORKDIR /app

# Installer afhængigheder
COPY package.json package-lock.json ./
RUN npm install

# Kopier kildekode og byg projektet
COPY . .
RUN npm run build

# Trin 2: Production stage (Nginx)
FROM nginx:stable-alpine
# Kopier det byggede output fra forrige trin til Nginx' standard-mappe
COPY --from=build /app/dist /usr/share/nginx/html

# Eksponer port 80
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]