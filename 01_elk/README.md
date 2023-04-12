#EFK

![EFK Stack](https://www.elastic.co/guide/en/beats/libbeat/current/images/beats-platform.png)


> Elasticsearch es un motor de búsqueda y analítica distribuido, gratuito y abierto para todos los tipos de datos, incluidos textuales, numéricos, geoespaciales, estructurados y no estructurado


## Install Elastic
```
Download the Elasticsearch PGP key:

rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch 

Create an elasticsearch.repo file in /etc/yum.repos.d/ using Nano, VIM, or Emacs:

nano /etc/yum.repos.d/elasticsearch.repo

Add the following to the file:

[elastic-8.x]
name=Elastic repository for 8.x packages
baseurl=https://artifacts.elastic.co/packages/8.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md

Save changes.

Now install Elasticsearch:

sudo yum install --enablerepo=elasticsearch elasticsearch

Open port 9200 in your firewall: Firewalld, UFW, CSF

curl -X GET localhost:9200

```

## Install Filebeat

```
sudo yum install filebeat
sudo systemctl enable filebeat
```

### Configure Filebeat
```
Set the connection information in filebeat.yml

output.elasticsearch:
  hosts: ["https://myEShost:9200"]
  username: "filebeat_internal"
  password: "YOUR_PASSWORD" 

filebeat modules list
filebeat modules enable nginx
```

## Install Kibana

```
sudo yum install kibana 
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable kibana.service
sudo systemctl start kibana.service
sudo systemctl stop kibana.service

Kibana loads its configuration from the /etc/kibana/kibana.yml file by default.


Point your web browser to the machine where you are running Kibana and specify the port number. For example, localhost:5601 or http://YOURDOMAIN.com:5601.


```
