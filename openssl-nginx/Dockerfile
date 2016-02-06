FROM jordi/openssl
MAINTAINER Jordi Íñigo Griera

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html
# https://evilshit.wordpress.com/2013/06/19/how-to-create-your-own-pki-with-openssl/
# https://github.com/nginxinc/docker-nginx

RUN apt-get update
RUN openssl dhparam -out /etc/ssl/certs/dhparam.pem 4096
RUN apt-get install -y nginx gettext-base \
    && rm -rf /var/lib/apt/lists/*
# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log
COPY nginx.conf /etc/nginx/sites-available/default

WORKDIR /root
RUN mkdir -p  ee/private
RUN chmod 700 ee/private
ADD server.conf etc/server.conf
ADD bash_history .bash_history

EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]