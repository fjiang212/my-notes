# Minishift
## Installing Minishift in Windows
* Download the archive for your operating system from the [Minishift releases page](https://github.com/minishift/minishift/releases) and unpack it.
* Copy the contents of the directory to your preferred location.
* Add the minishift binary to your PATH environment variable.
* Start minishift
```
Set HOMEDRIVE=C:\Users\xxxx
setproxy
minishift delete
minishift config set vm-driver virtualbox 
minishift config set memory 4096
minishift start 
```
```
The server is accessible via web console at:
    https://192.168.99.101:8443

You are logged in as:
    User:     developer
    Password: <any value>

To login as administrator:
    oc login -u system:admin
```

# Openshift Client
## Installing openshift client in Windows
* Download the archive for your operating system from the [oc releases page](https://github.com/openshift/origin/releases/latest) and unpack it.
* Copy the contents of the directory to your preferred location.
* Add the oc binary to your PATH environment variable.

## OC Reference
* https://docs.openshift.com/enterprise/3.0/cli_reference/get_started_cli.html
* oc config view
* login
```
Set HOMEDRIVE=C:\Users\xxxx
oc login
```


# Architecture
![alt text](images/openshift_architecture.jpg)
