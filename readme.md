knecht-docker
=====

A local development build environment using mesos, marathon, jenkins and a lot of other stuff.

- [cadvisor](https://github.com/google/cadvisor)
- [docker-registry](https://docs.docker.com/registry/)
- [docker-registry-frontend](https://github.com/kwk/docker-registry-frontend)
- [elasticsearch](https://www.elastic.co/products/elasticsearch)
- [gitlab](https://github.com/sameersbn/docker-gitlab)
- [grafana](https://github.com/grafana/grafana)
- [influxdb](https://www.influxdata.com/time-series-platform/influxdb/)
- [jenkins](https://jenkins.io/)
- [kibana](https://www.elastic.co/products/kibana)
- [logspout](https://github.com/gliderlabs/logspout)
- [logstash](https://www.elastic.co/products/logstash)
- [marathon](https://mesosphere.github.io/marathon/)
- [marathon-lb](https://github.com/mesosphere/marathon-lb/)
- [mesos](https://mesos.apache.org/)
- [telegraf](https://www.influxdata.com/time-series-platform/telegraf/)
- [zookeeper](https://zookeeper.apache.org/)


![logo](https://raw.githubusercontent.com/theborakompanioni/knecht-docker/master/assets/diagram.jpg)

# getting started
```
> git clone https://github.com/theborakompanioni/knecht-docker.git
> cd knecht-docker
> docker-compose up
```

# environment

## build
- gitlab: [http://localhost:10080/](http://localhost:10080/)
- jenkins: [http://localhost:8081/](http://localhost:8081/)
- docker-registry: [https://localhost:8443/](https://localhost:8443/)

## deploy
- marathon: [http://localhost:8080/](http://localhost:8080/)
- mesos: [http://localhost:5050/](http://localhost:5050/)

## loadbalancing (work in progress)
- HAProxy: [http://localhost:11090/haproxy?stats](http://localhost:11090/haproxy?stats)

to use haproxy for docker containers use labels `"HAPROXY_GROUP":"external"` and e.g. `"HAPROXY_0_VHOST":"zero.example.com"`.

## metrics
- grafana: [http://localhost:18000/](http://localhost:18000/)
- influxdb: [http://localhost:18083/](http://localhost:18083/)

Telegraf sends metrics on:
- docker
- elasticsearch
- haproxy (marathonlb)

## logging
- kibana: [http://localhost:8084/](http://localhost:8084/)
- logspout: [http://localhost:8083/logs](http://localhost:8083/logs)

## monitoring
- cadvisor: [http://localhost:8082/](http://localhost:8082/)


# todo
- use telegraf (with httpjson input e.g. for marathon metrics) and influxdb to monitor metrics
- use marathon-lb as loadbalancer (work in progress)
- evaluate [consul](https://consul.io)

# troubleshooting
## "Connection refused"/"Name or service not known."
Use DOCKER_OPTS to modify the daemon startup options.

add following to entry to `/etc/defaut/docker`
- `DOCKER_OPTS="--dns 8.8.8.8"` (or a nameserver of your choice)

# known issues
- on startup marathonlb fails to establish a new connection ([Errno 111] Connection refused) to marathon.
  can take up to three minutes to reconnect successfully - triggers telegraf errors
- sometimes mesos-slave does not come up - can be fixed by removing directory `docker-data/mesosslave-stuff/tmp`

# links
- https://container-solutions.com/continuous-delivery-with-docker-on-mesos-in-less-than-a-minute/
- https://github.com/ContainerSolutions/cd_demo
- https://github.com/autopilotpattern
- https://sebest.github.io/post/using-travis-ci-to-build-docker-images/
- https://docs.mesosphere.com/1.7/usage/service-discovery/marathon-lb/usage/

Assets from [Container Solutions](https://github.com/ContainerSolutions) / [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
