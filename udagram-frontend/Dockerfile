FROM marcoturi/ionic:alpine AS ionic
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci

# Build project
COPY . .
RUN ionic build

FROM nginx:alpine

RUN rm -rf /usr/share/nginx/html/*

COPY --from=ionic /usr/src/app/www /usr/share/nginx/html