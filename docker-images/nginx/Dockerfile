FROM nginx:latest

RUN rm -rf /etc/nginx/conf.d/*

COPY silverstripe.conf /etc/nginx/conf.d/silverstripe.conf
COPY nginx.conf /etc/nginx/nginx.conf

WORKDIR /etc/nginx

EXPOSE 80 443

CMD ["nginx"]
