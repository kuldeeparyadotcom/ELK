# ELK
ELK Centralized logging solution


The following commands can be used to use this system.
Assumption: Home directory for this project is ~/ELK

Spin up Elasticsearch container (-p option is optional in this command)
sudo docker run --name myes -v ~/ELK/elasticsearch/config:/usr/share/config -v ~/ELK/elasticsearch/esdata:/usr/share/data  -p 9200:9200 -p 9300:9300 elasticsearch:1.5

Spin up Redis Container
sudo docker run --name myredis -d redis:3

Spin up kibana container
sudo docker run -it --name mykibana4 -p 5601:5601 --link myes:es -v ~/ELK/kibana/config:/kibana/config kuldeeparyadotcom/kibana4:snapshot

Spin up logstash server container
sudo docker run -it --name mylt --link myes:es --link myredis:redis -v ~/ELK/logstash/config:/config-dir logstash:1.4 logstash -f /config-dir/logstash.conf

Spin up logstash shipper container
sudo docker run -it --name myltshipper --link myes:es --link myredis:redis -v ~/ELK/logstash/configshipper:/config-dir logstash:1.4 logstash -f /config-dir/logstash.conf


Verfication
1. http://YourDockerHost:9200 (elasticsearch test)
2. http://YourDockerHost:5601 (kibana test)

If you need any additional information, please feel free to reach out KD.

Thanks!
KD
http://kuldeeparya.com
kuldeeparyadotcom@gmail.com
