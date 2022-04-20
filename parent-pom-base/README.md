# Spring-based parent POM.

Generic Maven 3 parent POM with lots of default configuration. It is pre-configured to handle the "org.ujar.*" software
stack in a suitable way.

The latest released version requires JDK 11 at build time.

To use it as your parent POM using the following snippet:

```xml
  <parent>
    <groupId>org.ujar.bom</groupId>
    <artifactId>parent-pom-base</artifactId>
    <version>0.0.7-SNAPSHOT</version>
  </parent>
```
