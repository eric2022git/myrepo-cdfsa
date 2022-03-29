FROM golang:1.17 AS builder

WORKDIR /app

ADD main.go .
ADD go.mod .
ADD go.sum .

# /app/main
RUN go build -o main main.go

FROM golang:1.17

WORKDIR /app

COPY --from=builder /app/main .
ADD public public
ADD templates templates

ENV APP_PORT=3000 INSTANCE_NAME="dov-go-b"

EXPOSE ${APP_PORT}

ENTRYPOINT ["./main"]