FROM jordi/openssl-with-dhparams
MAINTAINER Jordi Íñigo Griera

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html
# https://evilshit.wordpress.com/2013/06/19/how-to-create-your-own-pki-with-openssl/
# https://github.com/nginxinc/docker-nginx

RUN apt-get install -y nginx gettext-base \
    && rm -rf /var/lib/apt/lists/*
# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log
COPY nginx.conf /etc/nginx/sites-available/default

WORKDIR /root
RUN mkdir -p  server/private
RUN chmod 700 server/private
RUN mkdir certs
RUN mkdir reqs
RUN mkdir crl
RUN echo 'PS1="NGINX:$PS1"' >> /root/.bashrc

ADD server.conf config/server.conf
ADD bash_history .bash_history

EXPOSE 443 80
# CMD ["nginx", "-g", "daemon off;"]
CMD ["bash"]
