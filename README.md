# Docker Postgres Debezium Kafka

---
### Skills:`Docker` `Docker-compose` `Postgres` `Debezium` `Zookeeper` `Kafka`

---
### Task: Create the Kafka topics monitoring
    1. Kafka must produce topicks with changes in Postgres 
    2. Consume creted topics
---
## Progress of work:

1. [*Installing Docker*][1] infrastructure
2. Configure [*Dockerfile*][2] image configuration
3. Creating [*SQL initiation script*][3] to create and initiate test table
4. Configure [*Docker-compose*][4] services:
 * postgreSQL 13
 * zookeeper
 * kafka
 * debezium
5. Creating [*schema-registry configuration*][5] for `Debezium connect`
6. Initiating *`Docker-compose.yaml`*:

```shell
$ docker-compose up -d
```
7. Initiating connection between Postgres & debezium

```shell
curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" 127.0.0.1:8083/connectors/ --data "@debezium.json"
```
8. Test created connection:

```shell
curl -i http://127.0.0.1:8083/connectors/exampledb-connector
```

9. Initiate the kafka topics monitoring

```shell
docker run --tty --network kafka-net confluentinc/cp-kafkacat kafkacat -b kafka:9092 -C -s key=s -s value=avro -r http://schema-registry:8081 -t postgres.public.student
```

[1]:
[2]:
[3]:
[4]:
[5]:
[6]:
