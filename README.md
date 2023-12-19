# Spring-based parent POM.

Generic Maven 3 parent POM with lots of default configuration. It is pre-configured to handle the "org.iqkv.*" software
stack in a suitable way.

The latest released version requires JDK 17 at build time.

To use it as your parent POM using the following snippet:

```xml
  <parent>
    <groupId>org.iqkv.boot</groupId>
    <artifactId>boot-parent-pom</artifactId>
    <version>24.0.0-SNAPSHOT</version>
  </parent>
```

## Code conventions

The code follows [Google Code Conventions](https://google.github.io/styleguide/javaguide.html). Code quality is measured by:

- Sonarqube
- [PMD](https://pmd.github.io/)
- [CheckStyle](https://checkstyle.sourceforge.io/)
- [SpotBugs](https://spotbugs.github.io/)

## Versioning

Project uses a three-segment [CalVer](https://calver.org/) scheme, with a short year in the major version slot, short month in the minor version slot, and micro/patch version in the third
and final slot.

```
YY.MM.MICRO
```

1. **YY** - short year - 6, 16, 106
1. **MM** - short month - 1, 2 ... 11, 12
1. **MICRO** -  "patch" segment
