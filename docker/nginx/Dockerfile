FROM nginx

COPY conf.d/nginx.conf /etc/nginx/nginx.conf
COPY conf.d/sites-avaliable/* /etc/nginx/conf.d/

WORKDIR /var/www/project

CMD ["nginx", "-g", "daemon off;"]
