FROM alpine:latest

MAINTAINER Jaime Navarro

RUN apk add --no-cache tzdata

ENV TZ=Europe/Madrid
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN wget -O /tmp/prometheus.tar.gz https://github.com/prometheus/prometheus/releases/download/v2.10.0/prometheus-2.10.0.linux-amd64.tar.gz
RUN addgroup -S prometheus && adduser -S -G prometheus prometheus
RUN mkdir -p /opt/prometheus
RUN chown prometheus:prometheus /opt/prometheus
RUN tar -xvf /tmp/prometheus.tar.gz -C /opt/prometheus --strip=1

COPY ./prometheus.yml /opt/prometheus/prometheus.yml

USER prometheus
WORKDIR /opt/prometheus
CMD /opt/prometheus/prometheus --config.file=/opt/prometheus/prometheus.yml --log.level=info

EXPOSE 9090
