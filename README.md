# OpenSSL Containers

This are Docker Images to generate Root-CA, TLS-Server containers.

They are based on [OpenSSL PKI Tutorial](https://pki-tutorial.readthedocs.org/en/latest/simple/index.html), and use OpenSSL toolkit.

It has pedagogical purposes to follow the PKI part of the [Introduction to Cryptography course](https://github.com/jig/crypto)

# Instructions

To log into the CA container:

``` 
$ docker run --name CA -ti jordi/openssl-ca
```

to log into the TLS-Server/nginx container:

```
$ docker run --name NGINX -p 443:443 -ti jordi/nginx
```

on all these containers you can scroll up throught `bash history` to use the recomended
shell commands.

To relaunch the created CA instance:

```
$ docker rm CA
$ docker start CA 
$ docker attach CA 
```

# License

MIT licensed

Copyright (C) 2016 Jordi Íñigo Griera