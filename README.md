## Project Overview

This project demonstrates a basic Apache Kafka setup using Docker and Docker Compose. It showcases real-time message streaming using Kafka Console Producer and Kafka Console Consumer within Docker containers.

The setup includes:
* Apache Kafka broker
* Apache Zookeeper
* A sample Kafka topic
* Console-based producer and consumer to send and receive messages
This project is intended for learning and demonstration purposes to understand Kafka message flow using Dockerized services.

## Prerequisites

Ensure the following are installed on your system:
* Docker
* Docker Compose
* Windows PowerShell or any terminal with Docker access


## Starting the Kafka Environment

To start Kafka and Zookeeper containers in detached mode, run:
```
docker-compose up -d
```
This command initializes all required services in the background.


## Verifying Running Containers

To check whether the containers are running:
```
docker ps
```
You should see Kafka and Zookeeper containers listed.


## Creating a Kafka Topic

Create a Kafka topic named `demo-topic` using the following command:
```
docker exec -it kafka kafka-topics --create --topic demo-topic --bootstrap-server localhost:29092 --partitions 1 --replication-factor 1
```
This creates a topic with one partition and one replica.


## Running the Kafka Consumer (Command Prompt 1)

Open a new terminal window and run the following command to start the consumer:
```
docker exec -it kafka kafka-console-consumer --topic demo-topic --from-beginning --bootstrap-server localhost:29092
```
This consumer listens to all messages from the beginning of the topic.


## Running the Kafka Producer (Command Prompt 2)

Open another terminal window and run the following command to start the producer:
```
docker exec -it kafka kafka-console-producer --topic demo-topic --bootstrap-server localhost:29092
```
You can now type messages in the producer terminal. Each message sent will be immediately received by the consumer.


## Example Messages

Sample messages sent by the producer:
```
User login event received
Processing payment transaction
Order placed successfully
Inventory updated in real time
```
These messages will appear instantly in the consumer terminal, demonstrating real-time message streaming.


## Stopping the Kafka Environment

To stop and remove all running containers:
```
docker compose down
```
This cleanly shuts down Kafka and Zookeeper services.


## Conclusion

This project provides a simple and effective way to understand Kafka’s producer-consumer model using Docker. It is suitable for beginners who want hands-on experience with Kafka message streaming in a containerized environment.
