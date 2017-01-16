FROM jordi/nginx
MAINTAINER Jordi Íñigo Griera

RUN apt-get update && apt-get -y install letsencrypt

RUN echo 'PS1="NGINX:$PS1"' >> /root/.bashrc
RUN echo "alias ll='ls -l'" >> /root/.bashrc
RUN bash -c "history -a"
