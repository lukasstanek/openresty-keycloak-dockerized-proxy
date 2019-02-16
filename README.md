# Automated Docker reverse proxy

Start nginx proxy which reverse proxies to all containers which specify the
```VIRTUAL_HOST``` environment variable.  
Additionally you can specify a PORT with ```VIRTUAL_PORT```    
The proxied port has to be EXPOSED in the Dockerfile.

```
docker-compose -p nginx up -d
```

docs: https://github.com/jwilder/nginx-proxy

## SSL

### lets encrypt
you can use letsencrypt the .encrypt docker file to automatically obtain ssl certs.

specify       
* LETSENCRYPT_HOST
* LETSENCRYPT_EMAIL

The host should the the same as VIRTUAL_HOST of your service.

### Selfsigned
If you want to use selfsigned certificates follow the instructions below

From nginx proxy readme:  
The contents of /path/to/certs should contain the certificates and private keys for any virtual hosts in use. The certificate and keys should be named after the virtual host with a .crt and .key extension. For example, a container with VIRTUAL_HOST=foo.bar.com should have a foo.bar.com.crt and foo.bar.com.key file in the certs directory.
