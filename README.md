# Generate Certificate for redis

## Using OpenSSL

### Create a private key
```shell
openssl genrsa -out redis.key 2048
```

### Create a certificate signing request
```shell
openssl req -new -key redis.key -out redis.csr
```

### Sign the private key using your certificate authority
```shell
openssl x509 -req -in redis.csr -signkey redis.key -out redis.pem

# for production
openssl x509 -req -in redis.csr -signkey redis.key -out redis.pem -days 365 -nodes
```
