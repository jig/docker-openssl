FROM jordi/ubuntu
MAINTAINER Jordi Íñigo Griera

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html
RUN apt-get update && apt-get -y install openssl

RUN echo "alias ll='ls -l'" >> /root/.bashrc
RUN bash -c "history -a"
