FROM node:10.17.0-alpine as node
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
ARG configuration
RUN npm run build -- --configuration $configuration
FROM nginx:1.17.5-alpine
COPY --from=node /usr/src/app/dist /usr/share/nginx/html