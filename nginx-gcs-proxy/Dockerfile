FROM nginx:1.15.8
RUN apt-get update \
    && apt-get install -y \
        wget \
    && rm -r /var/lib/apt/lists/*
ENV DOCKERIZE_VERSION v0.6.0
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz
COPY nginx.conf.tmpl /etc/nginx/nginx.conf.tmpl

ENV GCS_BUCKET " "
ENV LISTEN_PORT "8080"

ENV REDIRECT_404_TO_INDEX "false"
ENV OBJECT_PREFIX ""

ENV PROXY_CACHE "false"
ENV PROXY_CACHE_DURATION "30m"
ENV PROXY_CACHE_INACTIVE "1h"

ENV CACHE_CONTROL "none"
ENV CACHE_CONTROL_DURATION "1h"

ENV CORS "false"
ENV CORS_ALLOWED_ORIGINS "*"

ENV SERVICE_WORKER_FILENAME "sw\.js"

ENTRYPOINT ["dockerize", \
            "-template", \
            "/etc/nginx/nginx.conf.tmpl:/etc/nginx/nginx.conf"]
CMD ["nginx", \
    "-g", \
    "daemon off;"]
