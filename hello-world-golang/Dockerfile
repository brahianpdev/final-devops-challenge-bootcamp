FROM golang:1.12-alpine AS build_base

RUN apk add --no-cache git

WORKDIR /tmp/hello-world-golang

COPY . .

RUN CGO_ENABLED=0 go test -v

RUN go build -o ./out/hello-world-golang .

FROM alpine:3.9 
RUN apk add ca-certificates

COPY --from=build_base /tmp/hello-world-golang/out/hello-world-golang /app/hello-world-golang

EXPOSE 3002

CMD ["/app/hello-world-golang"]