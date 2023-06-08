FROM debian:buster

RUN apt-get update && apt-get install -y nginx \
					openssl
				
RUN mkdir /etc/nginx/ssl
RUN openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes \
					-out /etc/nginx/ssl/hdemin.crt\
					-keyout /etc/nginx/ssl/hdemin.key\
					-subj "/C=Fr/SR=Angouleme/L=Angouleme/O=42/OU=hde-min/CN=hde-min"

COPY ./conf/nginx.conf /etc/nginx/conf.d

RUN mkdir -p /run/nginx

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
