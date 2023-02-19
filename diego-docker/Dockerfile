FROM openjdk:8-jre-alpine

RUN apk add --no-cache bash gettext nmap-ncat openssl busybox-extras libc6-compat


# Rocketmq home
ENV ROCKETMQ_HOME  /rocketmq

WORKDIR  ${ROCKETMQ_HOME}

# Copie a pasta bin para o container
COPY ./distribution/ ${ROCKETMQ_HOME}


# Configurar nomesrv
RUN chmod +x ${ROCKETMQ_HOME}/bin/mqnamesrv
RUN echo "rocketmq.namesrv.addr=127.0.0.1:9876" > ${ROCKETMQ_HOME}/conf/broker.conf

# Configurar broker
RUN chmod +x ${ROCKETMQ_HOME}/bin/mqbroker
RUN echo "rocketmq.broker.cluster.name=rocketmq-cluster" > ${ROCKETMQ_HOME}/conf/broker.conf
RUN echo "rocketmq.broker.name=broker-a" > ${ROCKETMQ_HOME}/conf/broker.conf
RUN echo "rocketmq.broker.id=0" > ${ROCKETMQ_HOME}/conf/broker.conf
RUN echo "rocketmq.broker.ip=127.0.0.1" > ${ROCKETMQ_HOME}/conf/broker.conf
RUN echo "rocketmq.broker.port=10911" > ${ROCKETMQ_HOME}/conf/broker.conf

EXPOSE 9876 10911

CMD ["${ROCKETMQ_HOME}/bin/mqnamesrv"]
WORKDIR ${ROCKETMQ_HOME}/bin