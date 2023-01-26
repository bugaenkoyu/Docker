FROM nginx
LABEL maintainer="bugaenko"

RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN sed -i "0,/nginx/s/nginx/docker-nginx/i" /usr/share/nginx/html/index.html

COPY index.html /usr/share/nginx/html

CMD ["nginx"]

EXPOSE 80
