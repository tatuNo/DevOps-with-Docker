FROM golang:1.16

WORKDIR /usr/src/app

EXPOSE 8080

COPY . .

RUN go build

RUN useradd -m appuser

USER appuser

ENV REQUEST_ORIGIN=http://localhost

CMD ["./server"]