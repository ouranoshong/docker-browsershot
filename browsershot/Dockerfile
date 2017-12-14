FROM ouranoshong/shot-swoole-supervisord

LABEL name="ouranoshong@outlook.com"

COPY ./swoole.ini /etc/php/7.1/cli/conf.d/20-swoole.ini

ARG SUPERVISORD_CONFIG=supervisord.conf
COPY ${SUPERVISORD_CONFIG} /etc/supervisord.conf

# ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]