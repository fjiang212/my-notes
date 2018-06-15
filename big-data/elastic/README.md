# Installation 
## Ubuntu
* Install steps
    * https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-16-04
    * https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04

```
## Prepare JRE
sudo apt-get update
sudo apt-get install default-jre
sudo update-alternatives --config java

## Install elasticserch
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.3.0.deb
sudo dpkg -i elasticsearch-6.3.0.deb
sudo systemctl enable elasticsearch.service
sudo service elasticsearch start

## Install Kibana
wget https://artifacts.elastic.co/downloads/kibana/kibana-6.3.0-amd64.deb
sudo dpkg -i kibana-6.3.0-amd64.deb
sudo systemctl enable kibana.service
sudo service kibana start
```

# Unit Test
* https://github.com/elastic/solit
* https://github.com/fxdgear/solit-examples

