# Key Concepts
## cryptography
* **Symmetric-key cryptography**, where a single key is used for encryption and decryption. Symmetric-key cryptography refers to encryption methods in which both the sender and receiver share the same key (or, less commonly, in which their keys are different but related in an easily computable way).
* **Public-key cryptography, or asymmetric cryptography** , is any cryptographic system that uses pairs of keys: public keys which may be disseminated widely, and private keys which are known only to the owner. This accomplishes two functions: `authentication`, where the public key verifies that a holder of the paired private key sent the message, and `encryption`, where only the paired private key holder can decrypt the message encrypted with the public key.

# SSH
## Concepts
* **Secure Shell (SSH)** is a cryptographic network protocol for operating network services securely over an unsecured network
* **PEM** or Privacy Enhanced Mail is a Base64 encoded DER certificate.  PEM certificates are frequently used for web servers as they can easily be translated into readable data using a simple text editor.  Generally when a PEM encoded file is opened in a text editor, it contains very distinct headers and footers. PEM is a widely used encoding format for security certificates. Syntax and content is defined by X.509 v3 standards for digital certificates, defined in IETF RFC 5280 specifications. The main file extensions are **.pem, .crt, .ca-bundle.**

## Config file
* [OpenSSH/Client Configuration Files](https://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files)

## Set Up SSH Keys
* Login client machine as user **demo**
* Create the RSA Key Pair

```
$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/demo/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
[Private key]Your identification has been saved in /home/demo/.ssh/id_rsa.
[public key]Your public key has been saved in /home/demo/.ssh/id_rsa.pub.
```

* Copy the Public Key

Option 1: copy the public key into the new machine's authorized_keys file with the ssh-copy-id command

```
$ ssh-copy-id demo@198.51.100.0
```

Option 2: paste in the keys using SSH

```
cat ~/.ssh/id_rsa.pub | ssh demo@198.51.100.0 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```
* Connect to server machine without password

```
ssh demo@198.51.100.0
```

## Login with private key 

```
chmod 400 /path/my-key-pair.pem
ssh -i /path/my-key-pair.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com

```
