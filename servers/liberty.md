# Installation
* Download Liberty https://developer.ibm.com/wasdev/downloads/download-latest-stable-websphere-liberty-runtime/
* Create etc/repositories.properties https://stackoverflow.com/questions/37610212/cwwkf1219e-the-ibm-websphere-liberty-repository-cannot-be-reached
* Install additional features
```
bin/installUtility install adminCenter-1.0
bin/installUtility install javaee-7.0
```
* Start the server using:
```
bin/server start 
```
* To deploy an application, copy the .war file to the server’s dropins directory: usr/servers/server-name/dropins

# Eclipse 
https://www.ibm.com/blogs/bluemix/2016/05/liberty-and-eclipse-installing-dev-environment-p9/

