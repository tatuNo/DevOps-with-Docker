FROM golang:1.16-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN apk update --no-cache && \
    go build && \
    adduser -S appuser

USER appuser

ENV REQUEST_ORIGIN=http://localhost

CMD ["./server"]