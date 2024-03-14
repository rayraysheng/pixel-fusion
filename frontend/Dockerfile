# Base Node image
FROM node:14 AS development
WORKDIR /app
COPY ./frontend/package*.json ./
RUN npm install
COPY ./frontend/ .
CMD ["npm", "start"]

# Production build
FROM node:14 as build
WORKDIR /app
COPY --from=development /app ./
RUN npm run build

# Nginx to serve the build
FROM nginx:alpine as production
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
