# Spring Prometheus

Prometheus is an open-source technology designed to provide monitoring and alerting functionality for cloud-native environments, including Kubernetes. It can collect and store metrics as time-series data, recording information with a timestamp. It can also collect and record labels, which are optional key-value pairs.

Key features of Prometheus include:

- Multidimensional data model – Using time-series data, which is identified by metric name and key-value pairs.
- PromQL – A flexible querying language that can leverage the multi-dimensional data model.
- No reliance on distributed storage – All single server nodes remain autonomous.
- Pull model – Prometheus can collect time-series data by actively “pulling” data over HTTP.
- Pushing time-series data – Available through the use of an intermediary gateway.
- Monitoring target discovery – Available through static configuration or service discovery.
- Visualization – Prometheus offers multiple types of graphs and dashboards.

## Setup

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
    <scope>runtime</scope>
</dependency>
```

```yml
spring:
    application:
        name: spring-promotheus
info:
    application:
        name: Spring Prometheus
management:
    endpoints:
        web:
            exposure:
                include: health,info,prometheus
    info:
        env:
            enabled: true
```
