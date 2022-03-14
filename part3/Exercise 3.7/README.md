# https://github.com/docker-hy/ml-kurkkumopo-frontend

# Before 1.1GB

```FROM node:12.16.2

WORKDIR /usr/src/app

COPY . .

RUN npm ci

RUN npm run build
RUN npm install -g serve

EXPOSE 3000

CMD ["serve", "-s", "-l", "3000", "build"]
```

# After 99.8MB

```FROM node:12.16.2 as build

WORKDIR /usr/src/app

COPY . .

RUN npm ci && \
    npm run build

FROM node:12-alpine

WORKDIR /usr/src/app

RUN npm install -g serve && \
    adduser -S user

COPY --from=build /usr/src/app/build /usr/src/app/build

USER user

EXPOSE 3000

CMD ["serve", "-s", "-l", "3000", "build"]
```


