FROM nginx:alpine

LABEL name="ouranoshong"
LABEL email="ouranoshong@outlook.com"

COPY certs/* /etc/nginx/certs/
COPY nginx.conf /etc/nginx/
COPY sites/*.conf /etc/nginx/sites-available/

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data

ARG PHP_UPSTREAM_CONTAINER=browsershot
ARG PHP_UPSTREAM_PORT=9501

# Set upstream conf and remove the default conf
RUN echo "upstream back.end { server ${PHP_UPSTREAM_CONTAINER}:${PHP_UPSTREAM_PORT}; }" > /etc/nginx/conf.d/upstream.conf \
    && rm /etc/nginx/conf.d/default.conf

CMD ["nginx"]

EXPOSE 80 443
