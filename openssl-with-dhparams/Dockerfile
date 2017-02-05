FROM jordi/openssl
MAINTAINER Jordi Íñigo Griera

WORKDIR /root
RUN mkdir /root/dhparams
RUN openssl dhparam -out /root/dhparams/dhparam.pem 3072
