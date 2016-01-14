FROM jordi/openssl
MAINTAINER Jordi Íñigo Griera

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html

WORKDIR /root
RUN mkdir -p ca/private ca/db crl certs
RUN chmod 700 ca/private
RUN cp /dev/null ca/db/ca.db
RUN cp /dev/null ca/db/ca.db.attr
RUN echo 01 > ca/db/ca.crt.srl
RUN echo 01 > ca/db/ca.crl.srl

ADD ca.conf etc/ca.conf

RUN echo "openssl req -new -config etc/ca.conf -out ca/ca.csr -keyout ca/private/ca.key" >> .bash_history
RUN echo "openssl ca -selfsign -config etc/ca.conf -in ca/ca.csr -out ca/ca.crt -extensions ca_ext" >> .bash_history

# RUN openssl req -new -config etc/ca.conf -out ca/ca.csr -keyout ca/private/ca.key
# RUN openssl ca -selfsign -config etc/ca.conf -in ca/ca.csr -out ca/ca.crt -extensions ca_ext
