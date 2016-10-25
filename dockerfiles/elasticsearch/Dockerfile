FROM openjdk:8-jdk

RUN apt-get update && \
    apt-get install -y wget

RUN (cd /tmp && \
    wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.0.tar.gz -O pkg.tar.gz && \
    tar zxf pkg.tar.gz && mv elasticsearch-* /opt/elasticsearch &&\
    rm -rf /tmp/*)
COPY elasticsearch.yml /opt/elasticsearch/config/elasticsearch.yml
EXPOSE 9200
EXPOSE 9300
VOLUME /opt/elasticsearch/data
ENTRYPOINT ["/opt/elasticsearch/bin/elasticsearch"]
CMD []
