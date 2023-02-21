FROM openjdk:8-jre-alpine

# Install bash
RUN apk add --no-cache bash

# Copy the Kafka distribution archive and extract it
COPY ./core/build/distributions/kafka_2.13-3.4.0-SNAPSHOT.tgz /tmp
RUN tar -xzf /tmp/kafka_2.13-3.4.0-SNAPSHOT.tgz -C /opt
RUN mv /opt/kafka_2.13-3.4.0-SNAPSHOT /opt/kafka

# Expose the Kafka and ZooKeeper ports
EXPOSE 9092 2181

# Set the working directory to Kafka's bin directory
WORKDIR /opt/kafka/bin

# Start the Kafka broker in ZooKeeper mode
CMD ["/bin/bash", "-c", "./kafka-server-start.sh ../config/zookeeper.properties"]