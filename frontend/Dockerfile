# Stage 1: Build
FROM node:20 AS build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

# Stage 2: Serve with nginx
FROM nginx:1.25-alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
