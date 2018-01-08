* https://github.com/elastic/solit
* https://github.com/fxdgear/solit-examples

```
[root@localhost vagrant]# rpm -i elasticsearch-5.6.3.rpm
warning: elasticsearch-5.6.3.rpm: Header V4 RSA/SHA512 Signature, key ID d88e42b4: NOKEY
Creating elasticsearch group... OK
Creating elasticsearch user... OK
### NOT starting on installation, please execute the following statements to configure elasticsearch service to start automatically using systemd
 sudo systemctl daemon-reload
 sudo systemctl enable elasticsearch.service
### You can start elasticsearch service by executing
 sudo systemctl start elasticsearch.service
[root@localhost vagrant]#  sudo systemctl daemon-reload
[root@localhost vagrant]#  sudo systemctl enable elasticsearch.service
Created symlink from /etc/systemd/system/multi-user.target.wants/elasticsearch.service to /usr/lib/systemd/system/elasticsearch.service.
```
