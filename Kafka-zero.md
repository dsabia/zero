### for WINDOWS

_from this article: https://dzone.com/articles/running-apache-kafka-on-windows-os_  
download zookeeper  
download kafka

#### setup zookeeper
in C:\workspaces\void\Kafka zero\c\zookeeper-3.4.12  
/conf -> zoo_sample.cnf -> rename first in zoo.cnf  
/conf/zoo.cfg -> dataDir=C:\\workspaces\\void\\Kafka zero\\c\\zookeeper-3.4.12\\data  

add env variable
ZOOKEEPER_HOME=C:\workspaces\void\Kafka zero\c\zookeeper-3.4.12

open zookeeper using  
```
zkserver
```

#### setup kafka
in C:\workspaces\void\Kafka zero\c\kafka_2.11-1.1.0  
/conf/server.properties -> log.dirs=C:\\workspaces\\void\\Kafka zero\\c\\kafka_2.11-1.1.0\\kafka-logs  

cd "workspaces\void\Kafka zero\c\kafka_2.11-1.1.0"
```
bin\windows\kafka-server-start.bat config\server.properties
```

#### ... and now is up and Running!!!
### Create topic
```
bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
```
##### create producer
```
bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic test
```
##### and consumer
```
bin\windows\
kafka-console-consumer.bat --zookeeper localhost:2181 --topic test
```
bin\windows\

#### misc
_list topics_
```
bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
```
_describe topics_
```
bin\windows\kafka-topics.bat --describe --zookeeper localhost:2181 --topic test
```
_read message from beginning_
```
bin\windows\kafka-console-consumer.bat --zookeeper localhost:2181 --topic test --from-beginning
```
_delete topics_
```
bin\windows\kafka-run-class.bat kafka.admin.TopicCommand --delete --topic test --zookeeper localhost:2181
```
