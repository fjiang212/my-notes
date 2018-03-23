# Installing Minishift in Windows
## Download
* Download the archive for your operating system from the [Minishift releases page](https://github.com/minishift/minishift/releases) and unpack it.
* Copy the contents of the directory to your preferred location.
* Add the minishift binary to your PATH environment variable.
## Clean up minishift
* Delete minishift
```
minishift delete
```
* Close Virtual Box
* Delete `.minishift` and `.kube` under HOME DRIVE
## Start minishift
```
Set HOMEDRIVE=C:\Users\xxxx
setproxy
minishift config set vm-driver virtualbox 
minishift config set memory 4096
minishift config set http-proxy http://user:pwd@ip:pord
minishift config set https-proxy https://user:pwd@ip:pord
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

## Use OC
* download the latest oc tool:  https://github.com/openshift/origin/releases/latest
* Login to minishift VM
```
minishift ssh
Login as docker/tcuser
sudo su
```
