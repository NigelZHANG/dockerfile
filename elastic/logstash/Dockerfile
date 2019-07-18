FROM anapsix/alpine-java:8

RUN apk update && \
    apk upgrade && \
    apk add ruby=2.5.5-r0 && \
    rm -rf /var/cache/apk/* /tmp/*

RUN cd / && \
    wget https://artifacts.elastic.co/downloads/logstash/logstash-6.2.3.zip && \
    unzip logstash-6.2.3.zip && cd logstash-6.2.3 && \
    bin/logstash-plugin install logstash-input-jdbc && \
    bin/logstash-plugin install logstash-output-elasticsearch && \
    wget https://cdn.mysql.com//Downloads/Connector-J/mysql-connector-java-5.1.46.zip && \
    unzip mysql-connector-java-5.1.46.zip && \
    rm -rf mysql-connector-java-5.1.46.zip && \
    cd .. && rm -rf logstash-6.2.3.zip

CMD ["/logstash-6.2.3/bin/logstash"]