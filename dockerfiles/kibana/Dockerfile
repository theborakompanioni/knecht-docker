FROM nginx:1
RUN apt-get update && apt-get install -y wget ca-certificates
RUN wget https://download.elasticsearch.org/kibana/kibana/kibana-3.1.2.tar.gz -O /tmp/kibana.tar.gz && \
    cd /tmp && tar zxf kibana.tar.gz && mv kibana-*/* /usr/share/nginx/html/

# replace default into dashboard with logstash dashboard
RUN cp /usr/share/nginx/html/app/dashboards/logstash.json /usr/share/nginx/html/app/dashboards/default.json

EXPOSE 80
