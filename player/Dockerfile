FROM golang:latest

WORKDIR /app
RUN apt-get update

COPY ./go.mod .
RUN go mod tidy

CMD go run ./cmd/main.go