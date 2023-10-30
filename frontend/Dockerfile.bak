# Stage 1: Build the production app
FROM node:18-alpine

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

RUN npm run build

# Stage 2: Serve the production app
FROM nginx:latest

COPY --from=0 /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
