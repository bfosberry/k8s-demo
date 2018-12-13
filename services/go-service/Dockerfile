FROM golang:1.8.3-alpine AS src
MAINTAINER Aurelien PERRIER <a.perrier89@gmail.com>

ENV webserver_path /go/src/github.com/perriea/webserver/
ENV PATH $PATH:$webserver_path

WORKDIR $webserver_path
COPY webserver/ .

RUN go build -o /webserver .

FROM debian as runtime

WORKDIR /app
COPY --from=src /webserver /app/webserver
ENTRYPOINT /app/webserver

EXPOSE 8080
