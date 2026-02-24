# Stage 1: Build the Angular app
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# Stage 2: Serve with a lightweight Nginx container
FROM nginx:alpine
# Note: Check your angular.json for the exact output path (e.g., dist/frontend-app-name)
COPY --from=build /app/dist/angular-15-crud/usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]