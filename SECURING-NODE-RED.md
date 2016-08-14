# Node-red security

## Enable `node-red-admin`

http://nodered.org/docs/node-red-admin

Useful to get hashed passwords used to secure Node RED instance:
```
node-red-admin hash-pw
```

## Enable authentication and authorization

```js
adminAuth: {
    type: "credentials",
    users: [{
        username: "{USERNAME}",
        password: "##############.#####/####/##################",
        permissions: "*"
    }]
},
```

http://nodered.org/docs/security#editor--admin-api-security

## Add self-signed SSL

```bash
openssl genrsa -out privatekey.pem 1024
openssl req -new -key privatekey.pem -out private-csr.pem
openssl x509 -req -days 365 -in private-csr.pem -signkey privatekey.pem -out certificate.pem
```

```js
https: {
    key: fs.readFileSync('/home/{USERNAME}/.node-red/public/privatekey.pem'),
    cert: fs.readFileSync('/home/{USERNAME}/.node-red/public/certificate.pem')
},
```

http://industrialinternet.co.uk/node-red/adding-https-ssl-to-node-red/