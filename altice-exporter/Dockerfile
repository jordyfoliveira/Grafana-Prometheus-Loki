FROM golang:1.22-alpine AS build

RUN apk add --no-cache git ca-certificates

WORKDIR /src

RUN git clone https://github.com/Themimitoof/altice-exporter.git .

RUN go build -o /altice-exporter .

FROM alpine:3.20

RUN apk add --no-cache ca-certificates

COPY --from=build /altice-exporter /usr/local/bin/altice-exporter

EXPOSE 9876

ENTRYPOINT ["/usr/local/bin/altice-exporter"]
