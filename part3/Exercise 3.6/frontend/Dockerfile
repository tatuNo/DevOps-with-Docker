FROM node:16-alpine as build-stage

WORKDIR /app

COPY . .

RUN apk update --no-cache && \
    npm install && \
    REACT_APP_BACKEND_URL=http://localhost/api npm run build

FROM nginx:1.19-alpine

WORKDIR /app

COPY --from=build-stage /app/build /usr/share/nginx/html

RUN adduser -S user && \
    chown user /var/cache/nginx && \
    chown user /var/log/nginx && \
    chown user /etc/nginx/conf.d && \
    touch /var/run/nginx.pid && \
    chown user /var/run/nginx.pid

USER user