# KAFKA ZOOKEEPER

### Levantar Zookeeper: 
```shell script
bin\windows\zookeeper-server-start.bat config\zookeeper.properties
```

### Levantar Apache Kafka: 
```shell script
bin\windows\kafka-server-start.bat config\server.properties
```

### Crear tópico: 
```shell script
bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic topic-name
```

### Listar tópicos:
```shell script
bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
```

### Crear producer:
```shell script
bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic topic-name
``` 

### Crear consumer:
```shell script
bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic topic-name --from-beginning
``` 
