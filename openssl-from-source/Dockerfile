FROM ubuntu
MAINTAINER Jordi Íñigo Griera

# openssl is the only required thing to install
RUN apt-get update
RUN apt-get -y install wget
RUN apt-get -y install build-essential
RUN wget https://www.openssl.org/source/openssl-1.1.0.tar.gz
RUN tar xvf openssl-1.1.0.tar.gz
WORKDIR openssl-1.1.0
RUN ./Configure || true
RUN ./config 
RUN make && make install 

# installing an editor and netstat is not necessary, but is handy
RUN apt-get -y install nano vim emacs24-nox net-tools

RUN echo "alias ll='ls -l'" >> /root/.bashrc
RUN bash -c "history -a"
