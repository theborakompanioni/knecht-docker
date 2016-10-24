knecht-docker
=====

A local development build environment using mesos, marathon, jenkins and a lot of other stuff.

- [mesos](https://mesos.apache.org/)
- [marathon](https://mesosphere.github.io/marathon/)
- [marathon-lb](https://github.com/mesosphere/marathon-lb/)
- [docker-registry](https://docs.docker.com/registry/)
- [zookeeper](https://zookeeper.apache.org/)
- [elasticsearch](https://www.elastic.co/products/elasticsearch)
- [logstash](https://www.elastic.co/products/logstash)
- [kibana](https://www.elastic.co/products/kibana)
- [logspout](https://github.com/gliderlabs/logspout)
- [jenkins](https://jenkins.io/)


![logo](https://raw.githubusercontent.com/theborakompanioni/knecht-docker/master/assets/diagram.jpg)

# environment
- HAProxy: [http://localhost:11090/haproxy?stats](http://localhost:11090/haproxy?stats)
- marathon: [http://localhost:8080/](http://localhost:8080/)
- kibana: [http://localhost:8084/](http://localhost:8084/)

## marathon-lb (work in progress)
to use haproxy for docker containers use labels `"HAPROXY_GROUP":"external"` and `"HAPROXY_0_VHOST":"zero.example.com"`.

# todo
- use telegraf (with httpjson input e.g. for marathon metrics) and influxdb to monitor metrics
- use marathon-lb as loadbalancer (work in progress)

# links
- https://container-solutions.com/continuous-delivery-with-docker-on-mesos-in-less-than-a-minute/
- https://github.com/ContainerSolutions/cd_demo
- https://github.com/autopilotpattern
- https://sebest.github.io/post/using-travis-ci-to-build-docker-images/
- https://docs.mesosphere.com/1.7/usage/service-discovery/marathon-lb/usage/

Assets from [Container Solutions](https://github.com/ContainerSolutions) / [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
