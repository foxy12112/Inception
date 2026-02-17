FROM alpine:3.22

RUN apk update && apk upgrade && apk add --no-cache bash curl nginx openssl ca-certificates

RUN addgroup -g 101 -S nginx 2>/dev/null || true && adduser -u 100 -D -S -G nginx nginx 2>/dev/null || true

RUN mkdir -p /etc/nginx/ssl

RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout /etc/nginx/ssl/cert.key \
	-out /etc/nginx/ssl/cert.crt \
	-subj "/C=DE/ST=BW/L=Heilbronn/0=42/CN=$DOMAIN_NAME"

COPY ./tools/nginx-entrypoint.sh /usr/local/bin/

RUN chmod +x /usr/local/bin/nginx-entrypoint.sh

ENTRYPOINT [ "nginx-entrypoint.sh" ]

