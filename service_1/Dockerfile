FROM golang:1.22-alpine

RUN apk add --no-cache wget

WORKDIR /app

COPY . .

RUN go build -o main .

EXPOSE 8001

CMD ["./main"]

