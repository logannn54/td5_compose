FROM golang:1.20.5 AS builder

WORKDIR /app

COPY . .

RUN go mod tidy
RUN go build -o main .

FROM debian:bookworm-slim

WORKDIR /app

COPY --from=builder /app/main .

RUN apt-get update \
    && apt-get install -y --no-install-recommends redis-tools \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

EXPOSE 8080

CMD ["./main"]
