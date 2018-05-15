FROM jordi/nginx
MAINTAINER Jordi Íñigo Griera

RUN apt-get update && \
    apt-get -y install software-properties-common && \
    add-apt-repository -y ppa:certbot/certbot && \
    apt-get update && \
    apt-get -y install certbot

ADD nginx.conf /etc/nginx/sites-available/default
ADD bash_history .bash_history

RUN echo 'PS1="LETSENCRYPT:$PS1"' >> /root/.bashrc
RUN echo "alias ll='ls -l'" >> /root/.bashrc
RUN bash -c "history -a"
