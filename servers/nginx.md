# Installation
## Referencen
* Community: http://nginx.org/en/docs/
* Commercial Support: https://www.nginx.com

## Install trough yum repository
* https://www.nginx.com/resources/wiki/start/topics/tutorials/install/
* https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/
```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
```
```
yum install nginx
nginx -v
```

## Install through rpm



# Configuration
## Reserve proxy with kibana
```
server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    access_log  /var/log/nginx/kibana_server.access.log  main;

    location / {
        proxy_pass http://10.0.2.15:5601;
        proxy_read_timeout 90;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
}

```
## Reserve proxy with kibana + basic authentication
https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/

```
sudo yum install -y httpd-tools
sudo htpasswd -c /etc/nginx/.htpasswd nginx
```
```
server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    access_log  /var/log/nginx/kibana_server.access.log  main;

    auth_basic "Private Property";
    auth_basic_user_file /etc/nginx/.htpasswd;

    location / {
        #root   /usr/share/nginx/html;
        #index  index.html index.htm;
        proxy_pass http://10.0.2.15:5601;
        proxy_read_timeout 90;
    }
....
}
```

## Reserve proxy with kibana + basic authentication + ssl
```
server {
    listen       443;
    server_name  localhost;

        ssl on;
    ssl_certificate /etc/kibana/certs/kibana.crt;
    ssl_certificate_key /etc/kibana/certs/kibana.key;

    access_log  /var/log/nginx/kibana_server.access.log  main;

    auth_basic "Private Property";
    auth_basic_user_file /etc/nginx/.htpasswd;

    location / {
        proxy_pass https://10.0.2.15:5601;
        proxy_read_timeout 90;
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
}

```

## Issues
* permission denied:  https://stackoverflow.com/questions/23948527/13-permission-denied-while-connecting-to-upstreamnginx
