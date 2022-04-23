FROM nginx:1.21.6-alpine
LABEL autor="Carlos Carpintero" version="1.0"
RUN apk add nano
COPY ./default.conf /etc/nginx/conf.d/
WORKDIR /public_html
