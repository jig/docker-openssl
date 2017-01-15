# OpenSSL Containers

This are Docker Images to generate Root-CA, TLS-Server containers.

They are based on [OpenSSL PKI Tutorial](https://pki-tutorial.readthedocs.org/en/latest/simple/index.html), and use OpenSSL toolkit.

It has pedagogical purposes to follow the PKI part of the [Introduction to Cryptography course](https://github.com/jig/crypto)

# Instructions

You need to log in on any container to access `openssl` commands and operate CAs, servers, etc.

To log into the Root CA container:

``` 
$ docker run --name CAROOT -ti jordi/caroot
```

To log into the Subordinate CA container:

``` 
$ docker run --name CASUBOR -ti jordi/casubor
```

to log into the TLS-Server/nginx container:

```
$ docker run --name NGINX -p 443:443 -ti jordi/nginx
```

on all these containers you can scroll up throught `bash history` to use the recomended
shell commands.

To relaunch the created NGINX (or any other container) instance if logged out:

```
$ docker start NGINX 
$ docker attach NGINX 
```
The client (browser keys) can be generated with:

```
$ docker run --name BROWSER -ti jordi/openssl-browser
```


## Cleaning

If you can delete the container (with its keys)

```
$ docker rm NGINX 
```

And to remove everything:

```
$ docker rm -f $(docker ps -aq)
$ docker rmi -f $(docker images -q)
```


## nginx config

Current nginx config is rather restritive (for educational purposes). 
Only PFS cipher-suites with long DHE/ECHDE generators. 

CipherScan reports:

```
root@90cf3bde1d2c:/git/cipherscan# ./cipherscan https://example.lan
...........
Target: example.lan:443

prio  ciphersuite                  protocols  pfs                 curves
1     ECDHE-RSA-AES256-GCM-SHA384  TLSv1.2    ECDH,P-384,384bits  secp384r1
2     ECDHE-RSA-AES128-GCM-SHA256  TLSv1.2    ECDH,P-384,384bits  secp384r1
3     DHE-RSA-AES256-GCM-SHA384    TLSv1.2    DH,4096bits         None
4     DHE-RSA-AES128-GCM-SHA256    TLSv1.2    DH,4096bits         None
5     ECDHE-RSA-AES256-SHA384      TLSv1.2    ECDH,P-384,384bits  secp384r1
6     DHE-RSA-AES256-SHA256        TLSv1.2    DH,4096bits         None

Certificate: trusted, 4096 bits, sha256WithRSAEncryption signature
TLS ticket lifetime hint: 300
OCSP stapling: not supported
Cipher ordering: server
Curves ordering: server - fallback: no
Server supports secure renegotiation
Server supported compression methods: NONE
TLS Tolerance: yes

```

# License

MIT licensed

Copyright (C) 2016 Jordi Íñigo Griera