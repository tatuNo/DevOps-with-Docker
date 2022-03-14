FROM golang:1.16-alpine as build-stage

WORKDIR /usr/src/app

COPY . .

RUN apk update --no-cache && \
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build

ENV REQUEST_ORIGIN=http://localhost

FROM scratch

EXPOSE 8080

WORKDIR /usr/src/app/

COPY --from=build-stage /usr/src/app /usr/src/app

ENTRYPOINT ["/usr/src/app/server"]