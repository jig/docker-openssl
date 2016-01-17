FROM jordi/openssl

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html

WORKDIR /root
RUN mkdir -p  ee/private
RUN chmod 700 ee/private

ADD server.conf etc/server.conf

RUN echo \
    "export SAN=DNS:example.org\n" \
    "openssl req -new -config etc/server.conf -out ee/server.csr -keyout ee/private/server.key\n" \
    "cat ee/server.csr\n" \
    "openssl req -in ee/server.csr -noout -text\n" \
    "openssl s_server -key ee/private/server.key -cert ee/server.crt -accept 443 -www\n" >> .bash_history
