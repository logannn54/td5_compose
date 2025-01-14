FROM alpine:latest

RUN apk add --no-cache sqlite sqlite-dev

RUN mkdir -p /data

COPY init.sql /docker-entrypoint-initdb.d/

WORKDIR /data

CMD ["sqlite3", "/data/database.db"]
