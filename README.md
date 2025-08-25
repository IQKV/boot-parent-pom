# ✨ Spring Boot Parent POM

A comprehensive Maven parent POM designed specifically for Spring Boot applications in the `com.iqkv.*` ecosystem. This parent POM provides sensible defaults, standardized configurations, and integrated quality tools to streamline Java development.

## 🚀 Features

- **Spring Boot Integration**: Optimized for Spring Boot applications
- **Java 21 Support**: Built for modern Java development
- **Code Quality**: Integrated with industry-standard quality tools
- **Standardized Configuration**: Consistent build configuration across projects
- **Development Tools**: Pre-configured formatters, linters, and commit hooks

## 📦 Usage

Add this parent POM to your Maven project:

```xml
<parent>
  <groupId>com.iqkv.boot</groupId>
  <artifactId>boot-parent-pom</artifactId>
  <version>25.0.0-SNAPSHOT</version>
</parent>
```

## 📋 Requirements

- **Build Time**: JDK 21 or higher
- **Maven**: 3.6+ recommended
- **Node.js**: Required for development tooling (formatting, linting)

## 🔧 Code Quality & Standards

This parent POM enforces high code quality through multiple integrated tools:

### Code Style
- **[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)**: Consistent formatting and conventions
- **[Prettier](https://prettier.io/)**: Automated code formatting
- **[EditorConfig](https://editorconfig.org/)**: Cross-editor consistency

### Static Analysis
- **[SonarQube](https://docs.sonarsource.com/)**: Comprehensive code quality analysis
- **[PMD](https://pmd.github.io/)**: Source code analyzer for common programming flaws
- **[Checkstyle](https://checkstyle.sourceforge.io/)**: Coding standard compliance
- **[SpotBugs](https://spotbugs.github.io/)**: Static analysis for bug detection
- **[Qulice](https://www.qulice.com/)**: Aggregated quality control

### Git Hooks
- **[Husky](https://typicode.github.io/husky/)**: Git hooks management
- **[Commitlint](https://commitlint.js.org/)**: Conventional commit message validation
- **[lint-staged](https://github.com/okonet/lint-staged)**: Run linters on staged files

## 🛠️ Development

The project includes development automation tools:

- **Prettier**: Code formatting (`pnpm format`)
- **Release-it**: Automated releases with conventional changelog
- **Commit validation**: Ensures conventional commit format

## 📄 License

This project is licensed under the terms specified in the [LICENSE](LICENSE) file.

## 🤝 Contributing

1. Follow the established code conventions
2. Use conventional commit messages
3. Ensure all quality checks pass before submitting PRs
4. Update documentation as needed

---

*This parent POM is part of the IQKV ecosystem, designed to provide consistent and high-quality Java application development.*
`
