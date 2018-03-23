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
oc login -u system:admin
```


# Architecture
![alt text](../images/openshift_architecture.jpg)

# Openshift Development Guide
https://docs.openshift.com/container-platform/3.7/dev_guide/index.html

## Routes
https://docs.openshift.com/container-platform/3.7/architecture/networking/routes.html
```
oc get routes
oc get route/logstash
oc edit route logstash
```

* Using SSL: https://www.youtube.com/watch?v=rpT5qwcL3bE&list=PLaR6Rq6Z4Iqficb-XqeydZD_ZTD3XEwBp&index=18
1. Edge Termination
2. Passthrough Termination
3. Re-Encrpty Termination

## Secrets
https://docs.openshift.com/container-platform/3.7/dev_guide/secrets.html
```
oc get secrets
oc create secret generic database-user-name   --from-literal=database-user-name=acutal_user
oc create secret generic database-password    --from-literal=database-password=acutal_password
oc create secret generic keystoresecret --from-file=<jks file> 

# Create a new secret named my-secret with keys for each file in folder bar
oc create secret generic my-secret --from-file=path/to/bar
  
# Create a new secret named my-secret with specified keys instead of names on disk
oc create secret generic my-secret --from-file=ssh-privatekey= /.ssh/id_rsa --from-file=ssh-publickey= /.ssh/id_rsa.pub
  
# Create a new secret named my-secret with key1=supersecret and key2=topsecret
oc create secret generic my-secret --from-literal=key1=supersecret --from-literal=key2=topsecret
```

# Openshift Deployment Guide
https://blog.openshift.com/multiple-deployment-methods-openshift/
## Redeploy from git Dockerfile
```
oc delete bc --all
oc delete dc --all
oc delete service --all
oc delete is --all
oc delete pod --all

oc new-app https:/xxx.net/scm/app/test.git --name=test --context-dir=<dirname> -o yaml > myapp.yaml
oc create -f myapp.yaml
set environment  GIT_SSL_NO_VERIFY=true in the build
oc deploy test --latest -n <project name>
oc expose service myapp --hostname=myapp-project.example.com
```
