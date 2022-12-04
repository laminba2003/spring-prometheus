# Spring Prometheus

## Prometheus

Prometheus is an open-source technology designed to provide monitoring and alerting functionality for cloud-native environments, including Kubernetes. It can collect and store metrics as time-series data, recording information with a timestamp. It can also collect and record labels, which are optional key-value pairs.

Key features of Prometheus include:

- Multidimensional data model: Using time-series data, which is identified by metric name and key-value pairs.
- PromQL: A flexible querying language that can leverage the multi-dimensional data model.
- No reliance on distributed storage: All single server nodes remain autonomous.
- Pull model: Prometheus can collect time-series data by actively “pulling” data over HTTP.
- Pushing time-series data: Available through the use of an intermediary gateway.
- Monitoring target discovery: Available through static configuration or service discovery.
- Visualization: Prometheus offers multiple types of graphs and dashboards.

## Alertmanager

The Alertmanager handles alerts sent by client applications such as the Prometheus server. 
It takes care of deduplicating, grouping, and routing them to the correct receiver integrations such as email, Slack, PagerDuty, OpsGenie, or many other mechanisms thanks to the webhook receiver. 
It also takes care of silencing and inhibition of alerts.

## Grafana

Grafana allows you to query, visualize, alert on and understand your metrics no matter where they are stored. Create, explore, and share dashboards with your team and foster a data-driven culture:

- Visualizations: Fast and flexible client side graphs with a multitude of options. Panel plugins offer many different ways to visualize metrics and logs.
- Dynamic Dashboards: Create dynamic & reusable dashboards with template variables that appear as dropdowns at the top of the dashboard.
- Explore Metrics: Explore your data through ad-hoc queries and dynamic drilldown. Split view and compare different time ranges, queries and data sources side by side.
- Explore Logs: Experience the magic of switching from metrics to logs with preserved label filters. Quickly search through all your logs or streaming them live.
- Alerting: Visually define alert rules for your most important metrics. Grafana will continuously evaluate and send notifications to systems like Slack, PagerDuty, VictorOps, OpsGenie.
- Mixed Data Sources: Mix different data sources in the same graph! You can specify a data source on a per-query basis. This works for even custom datasources.

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


## Start the services

Run this command to start all services in the correct order.

```bash
$ docker-compose up -d
```

## Run the application

Run this command to start the application.

```
mvn spring-boot:run
```

## Stop the services

```bash
docker-compose down
```