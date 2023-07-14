FROM golang:1.19 as builder

WORKDIR /app
COPY ./src/main.go .

# Build
RUN CGO_ENABLED=0 GOOS=linux GOPROXY=https://proxy.golang.org go build -o goApp ./main.go

FROM alpine:latest

WORKDIR /app
COPY --from=builder /app/goApp .

# Run
CMD ["./goApp"]