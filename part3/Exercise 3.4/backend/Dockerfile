FROM golang:1.16-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN go build && \
    adduser -S appuser && \
    rm -rf /var/cache/apk/*

USER appuser

ENV REQUEST_ORIGIN=http://localhost

CMD ["./server"]