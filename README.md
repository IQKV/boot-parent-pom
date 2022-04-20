Generic Maven 3 parent POM with lots of default configuration. It is pre-configured to handle the "org.ujar.*" software
stack in a suitable way.

The latest released version requires JDK 11 at build time.

[![Build Status](https://drone.ujar.org/api/badges/ujar-org/bom/status.svg?ref=refs/heads/main)](https://drone.ujar.org/ujar-org/bom)

# Spring-based parent POM.

To use it as your parent POM using the following snippet:

```xml
  <parent>
    <groupId>org.ujar.bom</groupId>
    <artifactId>parent-pom-base</artifactId>
    <version>0.0.7-SNAPSHOT</version>
  </parent>
```

# Parent POM for all RESTful microservices.

```xml
  <parent>
    <groupId>org.ujar.bom</groupId>
    <artifactId>parent-pom-rest</artifactId>
    <version>0.0.7-SNAPSHOT</version>
  </parent>
```

# Asynchronous service parent POM for Apache Kafka.

```xml
  <parent>
    <groupId>org.ujar.bom</groupId>
    <artifactId>parent-pom-async-kafka</artifactId>
    <version>0.0.7-SNAPSHOT</version>
  </parent>
```
