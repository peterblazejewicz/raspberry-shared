# raspberry-shared

Shared configuration files for raspberry devices

## Transferring content

From remote to local:
```
scp pi@192.168.1.200:~/.vimrc .
```

## Create self-signed SSL Certificate

```
openssl genrsa -out privatekey.pem 1024
openssl req -new -key privatekey.pem -out private-csr.pem
openssl x509 -req -days 365 -in private-csr.pem -signkey privatekey.pem -out certificate.pem
```

## Author
@peterblazejewicz