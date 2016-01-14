# OpenSSL Containers

This are Docker Images to generate Root-CA, TLS-Server and TLS-Client containers.

They are based on [OpenSSL PKI Tutorial](https://pki-tutorial.readthedocs.org/en/latest/simple/index.html), and use OpenSSL toolkit.

It has pedagogical purposes to follow the PKI part of the [Introduction to Cryptography course](https://github.com/jig/crypto)

# Instructions

To log into the CA container:

``` 
$ docker run --name ROOT -ti jordi/openssl-ca
```

to log into the TLS-Server container:

```
$ docker run --name SERVER -p 443:443 -ti jordi/openssl-tlsserver
```

and to log into the TLS-Client container:

```
$ docker run --name CLIENT -ti jordi/openssl-tlsclient
```

on all these containers you can scroll up throught `bash history` to use the recomended
shell commands.

To relaunch the created CA instance:

```
$ docker rm ROOT
$ docker start ROOT 
$ docker attach ROOT 
```

# License

MIT licensed

Copyright (C) 2016 Jordi Íñigo Griera