FROM jordi/openssl
MAINTAINER Jordi Íñigo Griera

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html

WORKDIR /root
RUN mkdir -p ca/private ca/db crl certs reqs
RUN chmod 700 ca/private
RUN cp /dev/null ca/db/ca.db
RUN cp /dev/null ca/db/ca.db.attr
RUN echo 01 > ca/db/ca.crt.srl
RUN echo 01 > ca/db/ca.crl.srl
RUN echo 'PS1="CAROOT:$PS1"' >> /root/.bashrc

ADD ca.conf config/ca.conf
ADD bash_history .bash_history
