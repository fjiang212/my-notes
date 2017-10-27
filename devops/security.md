# Generate CA Signed certificate
## Create CSR
*	mkdir ~/machine01.example.com.ssl
*	cd ~/machine01.example.com.ssl
*	openssl genrsa -out ~/machine01.example.com.ssl/machine01.example.com.key 2048 && chmod 0600 machine01.example.com.key
*	openssl req -new -nodes -sha256 -config ~/machine01.example.com.ssl/SAN.conf -out ~/ machine01.example.com.ssl/machine01.example.com.csr

## Verify CSR and private key
* openssl req -text -noout -verify -in machine01.example.com.csr
* openssl rsa -in machine01.example.com.key -check

## Verify generated private key is matched with certificate
*	openssl rsa -noout -modulus -in server.key | openssl md5
*	openssl x509 -noout -modulus -in server.crt | openssl md5
