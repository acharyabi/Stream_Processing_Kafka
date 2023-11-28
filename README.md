
# Running Spark and Kafka Clusters on Docker

### 1. Build Required Images for running Spark

The details of how to spark-images are build in different layers can be created can be read through 
the blog post written by André Perez on [Medium blog -Towards Data Science](https://towardsdatascience.com/apache-spark-cluster-on-docker-ft-a-juyterlab-interface-418383c95445)

```bash
# Build Spark Images
./build.sh 
```

### 2. Create Docker Network & Volume

```bash
# Create Network
docker network  create kafka-spark-network

# Create Volume
docker volume create --name=hadoop-distributed-file-system
```

### 3. Run Services on Docker
```bash
# Start Docker-Compose (within for kafka and spark folders)
docker compose up -d
```
In depth explanation of [Kafka Listeners](https://www.confluent.io/blog/kafka-listeners-explained/)

Explanation of [Kafka Listeners](https://www.confluent.io/blog/kafka-listeners-explained/)

### 4. Stop Services on Docker
```bash
# Stop Docker-Compose (within for kafka and spark folders)
docker compose down
```

### 5. Helpful Comands
```bash
# Delete all Containers
docker rm -f $(docker ps -a -q)

# Delete all volumes
docker volume rm $(docker volume ls -q)
```




#Stream-Processing with Python

In this document, you will be finding information about stream processing using different Python libraries (kafka-python,confluent-kafka,pyspark, faust).

This Python module can be seperated in following modules.

1. Docker
Docker module includes, Dockerfiles and docker-compose definitions to run Kafka and Spark in a docker container. Setting up required services is the prerequsite step for running following modules.

2. Kafka Producer - Consumer Examples
Json Producer-Consumer Example using kafka-python library
Avro Producer-Consumer Example using confluent-kafka library
Both of these examples require, up-and running Kafka services, therefore please ensure following steps under docker-README

To run the producer-consumer examples in the respective example folder, run following commands

# Start producer script
python3 producer.py

# Start consumer script
python3 consumer.py