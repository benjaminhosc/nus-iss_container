FROM golang:1.23-alpine3.20 AS builder

WORKDIR /src

COPY go.* .
COPY main.go .

RUN CGO_ENABLED=0 go build =o main main.go

# container to run the application
FROM alpine:3.20

LABEL maintainers="benho"

WORKDIR /app

#copy the binary over from the build container
COPY --from=builder /src/main .
COPY public public
COPY templates templates

ENV PORT=3000 INSTANCE_NAME=my-dov-bear INSTANCE_HASH=my_dov_bear_hash

EXPOSE ${PORT}

ENTRYPOINT /app/main