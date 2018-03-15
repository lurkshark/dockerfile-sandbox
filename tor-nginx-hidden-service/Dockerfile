FROM alpine:latest

RUN apk add --no-cache tor nginx

COPY hidden-service.conf /etc/tor/torrc.d/hidden-service
COPY reverse-proxy.conf /etc/nginx/conf.d/default.conf
COPY service/* /var/lib/tor/service/
COPY entrypoint.sh /entrypoint.sh

RUN echo "%include /etc/tor/torrc.d/" | tee -a /etc/tor/torrc && \
    rm -f /var/lib/tor/service/.gitignore && \
    chmod 600 /var/lib/tor/service/* && \
    chmod 600 /var/lib/tor/service && \
    mkdir -p /run/nginx

ENTRYPOINT [ "/entrypoint.sh" ]
