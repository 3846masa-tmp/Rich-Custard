# Proxy using Docker API
# Usage: docker run -d -p 80:80 -e DOMAIN="example.com" -v /var/run/docker.sock:/var/run/docker.sock 3846masa/proxy

FROM dockerfile/ubuntu
MAINTAINER 3846masa <3846masahiro+git@gmail.com>

RUN apt update && apt install -y nginx-extras libjson-perl libjson-xs-perl

ADD nginx /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/perl_set /etc/nginx/sites-enabled/perl_set

RUN sed -i /etc/nginx/nginx.conf \
        -e "1i daemon off;" \
        -e "1i env HOSTNAME;" \
        -e "1i env DOMAIN;"

EXPOSE 80 443

CMD ["nginx"]
