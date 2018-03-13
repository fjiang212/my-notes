# Unix Security
## group
* By default, on CentOS 7, users who belong to the "wheel" group are allowed to use the sudo command.

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

# Generate keystore
* Create keystore
```
keytool -keystore server.keystore.jks -alias localhost -validity 365 -keyalg RSA -genkey
```
*	list keystore
```
keytool -list -v -keystore server.keystore.jks
```
*	Delete certificate
```
keytool -delete -alias localhost -keystore server.keystore.jks
```
*	combine private key and certricate to P12 ketstore
```
openssl pkcs12 -export -in server.crt -inkey server.key > server.p12
```
*	Import server.p12 to empty keystore with "Keystroe Explorer" or
```
Keytool  -importkeystore -srckeystore server.p12 -destkeystore server.keystore.jks -srcstoretype pkcs12 -destalias  kafkaserver
```
* Others
```
keytool -genkey -dname "CN=elk.dev.example.com, OU=example.com, O=EXAMPLE, L=TORONTO, ST=ONTARIO, C=CA" -alias elk -keyalg RSA -keysize 2048 -keystore elk.keystore -storepass password keytool -certreq -alias elk -file server.dev.example.com.csr -keystore server.keystore -storepass password
keytool -list -v -keystore C:\path-to-keystore\server.keystore
keytool -import -trustcacerts -alias elk -file C:\Certificate\certnew.p7b -keystore C:\path-to-keystore\server.keystore
```
# Add trust root certificate
http://kb.kerio.com/product/kerio-connect/server-configuration/ssl-certificates/adding-trusted-root-certificates-to-the-server-1605.html

# Trouble shooting
```
openssl s_client -connect machine01.dev.example.com.ssl:5145
openssl s_client -state -nbio -connect machine01.dev.example.com.ssl:5145
openssl s_client -state -nbio -connect machine01.dev.example.com.ssl:5145 -CAfile /path-to-certificate/chain.crt
openssl s_client -state -nbio -debug -connect  machine01.dev.example.com.ssl:5145 -CAfile /path-to-certificate/chain.crt
openssl s_client -state -nbio -connect machine01.dev.example.com.ssl:5045 -CAfile /path-to-certificate/chain.crt
openssl s_client -state -nbio -debug -connect  machine01.dev.example.com.ssl:5045 -CAfile /path-to-certificate/chain.crt
```
