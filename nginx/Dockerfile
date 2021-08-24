From nginx:latest

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY nginx/sites/*.conf /etc/nginx/sites-available/

WORKDIR /var/www/html
RUN chown -R www-data:www-data /var/www/html