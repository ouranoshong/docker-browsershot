FROM 'ouranoshong/browsershot'

LABEL name="ouranoshong@outlook.com"

RUN apt-get update -y \
    && apt-get install -y php7.0-dev php-pear \
    && pecl install swoole \
    && apt-get autoremove -y php7.0-dev php-pear \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY ./swoole.ini /etc/php/7.0/cli/conf.d/20-swoole.ini

RUN apt-get update -y \
    && apt-get install -y supervisor \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

EXPOSE 9501

ARG SUPERVISORD_CONFIG=supervisord.conf
COPY ${SUPERVISORD_CONFIG} /etc/supervisord.conf

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]