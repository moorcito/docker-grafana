FROM alpine:latest

MAINTAINER Jaime Navarro

RUN wget -O /tmp/prometheus.tar.gz https://github.com/prometheus/prometheus/releases/download/v2.9.2/prometheus-2.9.2.linux-amd64.tar.gz
RUN addgroup -S prometheus && adduser -S -G prometheus prometheus
RUN mkdir -p /opt/prometheus
RUN chown prometheus:prometheus /opt/prometheus
RUN tar -xvf /tmp/prometheus.tar.gz -C /opt/prometheus --strip=1

COPY ./prometheus.yml /opt/prometheus/prometheus.yml

USER prometheus
WORKDIR /opt/prometheus
CMD /opt/prometheus/prometheus --config.file=/opt/prometheus/prometheus.yml --log.level=info

EXPOSE 9090
