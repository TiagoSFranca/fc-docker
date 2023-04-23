FROM golang:latest AS build

WORKDIR /go/app

RUN apt-get update && apt-get install -y librdkafka-dev

COPY ./ ./

RUN CGO_ENABLED=0 GOOS=linux go build -o /build/cmd ./main.go

FROM scratch

COPY --from=build ./build/cmd/ ./main

ENTRYPOINT ["/main"]