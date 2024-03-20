FROM ubuntu:20.04
LABEL maintainer="jvitor.lr@hotmail.com"
RUN apt-get update && apt-get install nginx curl -y && rm -rf /var/lib/apt/lists/*
EXPOSE 80
WORKDIR /root
ADD https://github.com/prometheus/node_exporter/releases/download/v1.6.0/node_exporter-1.6.0.linux-amd64.tar.gz .
RUN tar -xzf node_exporter-1.6.0.linux-amd64.tar.gz && rm node_exporter-1.6.0.linux-amd64.tar.gz
COPY index.html /var/www/html/
WORKDIR /var/www/html
ENV APP_VERSION 1.0.0
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
HEALTHCHECK --timeout=2s CMD curl -f localhost || exit 1
