FROM nginx:alpine
RUN apk update && apk add bash openssl apache2-utils
RUN rm /etc/nginx/conf.d/* 
RUN mkdir /etc/nginx/ssl
RUN chmod 700 /etc/nginx/ssl
RUN cd /etc/nginx/ssl
RUN openssl req -x509 -nodes -days 365 -subj "/C=CA/ST=BC/O=Company, Inc./CN=mydomain.com" -addext "subjectAltName=DNS:mydomain.com" -newkey rsa:2048 -keyout /etc/nginx/ssl/proxy.key -out /etc/nginx/ssl/proxy.crt
RUN htpasswd -cb /etc/nginx/.htpasswd admin Password1
COPY proxy.conf /etc/nginx/conf.d/