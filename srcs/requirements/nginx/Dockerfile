FROM alpine:3.23

RUN apk update && apk upgrade && apk add --no-cache nginx openssl ca-certificates

RUN mkdir -p /etc/nginx/ssl

RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout /etc/nginx/ssl/cert.crt \
	-out /etc/nginx/ssl/cert.key \
	-subj "/C=DE/ST=BW/L=Heilbronn/0=42/CN=ldick.42.fr"

COPY tools/nginx-entrypoint.sh /usr/local/bin/

RUN chmod +x /usr/local/bin/nginx-entrypoint.sh

EXPOSE 443

ENTRYPOINT [ "nginx-entrypoint.sh" ]

