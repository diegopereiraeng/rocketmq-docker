FROM openjdk:8-jre-alpine

# Copie a pasta bin para o container
COPY ./distribution/bin /rocketmq

# Extrair o RocketMQ
#RUN tar -xzf /rocketmq.tar.gz -C /

# Configurar nomesrv
#RUN mv /apache-rocketmq-*-bin /rocketmq
RUN chmod +x /rocketmq/bin/mqnamesrv
RUN echo "rocketmq.namesrv.addr=127.0.0.1:9876" > /rocketmq/conf/broker.conf

# Configurar broker
RUN chmod +x /rocketmq/bin/mqbroker
RUN echo "rocketmq.broker.cluster.name=rocketmq-cluster" > /rocketmq/conf/broker.conf
RUN echo "rocketmq.broker.name=broker-a" > /rocketmq/conf/broker.conf
RUN echo "rocketmq.broker.id=0" > /rocketmq/conf/broker.conf
RUN echo "rocketmq.broker.ip=127.0.0.1" > /rocketmq/conf/broker.conf
RUN echo "rocketmq.broker.port=10911" > /rocketmq/conf/broker.conf

EXPOSE 9876 10911

CMD ["/rocketmq/bin/mqnamesrv"]
