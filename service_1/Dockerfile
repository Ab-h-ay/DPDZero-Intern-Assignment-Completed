FROM golang:1.22-alpine

WORKDIR /app

COPY . .

# Optional: only if go.mod not present
# RUN go mod init service1

RUN go build -o main .

EXPOSE 8001

CMD ["./main"]

