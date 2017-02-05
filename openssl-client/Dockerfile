FROM jordi/openssl
MAINTAINER Jordi Íñigo Griera

# https://pki-tutorial.readthedocs.org/en/latest/simple/index.html
# https://evilshit.wordpress.com/2013/06/19/how-to-create-your-own-pki-with-openssl/

WORKDIR /root
RUN mkdir -p  ee/private
RUN chmod 700 ee/private
RUN echo 'PS1="CLIENT:$PS1"' >> /root/.bashrc

ADD browser.conf config/browser.conf
ADD bash_history .bash_history
