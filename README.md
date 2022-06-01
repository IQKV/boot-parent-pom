# Spring-based parent POM.

[![Build Status](https://drone.ujar.org/api/badges/ujar-org/ujar-parent-pom/status.svg)](https://drone.ujar.org/ujar-org/ujar-parent-pom)

Generic Maven 3 parent POM with lots of default configuration. It is pre-configured to handle the "org.ujar.*" software
stack in a suitable way.

The latest released version requires JDK 17 at build time.

To use it as your parent POM using the following snippet:

```xml
  <parent>
    <groupId>org.ujar.parent</groupId>
    <artifactId>ujar-parent-pom</artifactId>
    <version>0.7.0-SNAPSHOT</version>
  </parent>
```
## Code conventions

The code follows [Google Code Conventions](https://google.github.io/styleguide/javaguide.html) without exceptions. Code quality is measured by:
- [Sonarqube](https://sonarqube.ujar.org/)
- [PMD](https://pmd.github.io/)
- [CheckStyle](https://checkstyle.sourceforge.io/)
- [SpotBugs](https://spotbugs.github.io/)
