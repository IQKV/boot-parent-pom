# AI Agent Development Guide

## Project Overview

**boot-parent-pom** — Maven parent POM for all iQKV Foundation Spring Boot services. Manages the full platform dependency tree: Spring Boot 4.x, Spring Cloud, Jakarta EE, persistence, messaging, observability, testing, and all plugin versions.

**Key characteristics:**

- Pure `pom` packaging — no Java source, no compiled artifacts
- All child services (`foundation-iam-service`, `foundation-cms-service`, `foundation-billing-service`, `foundation-gateway-service`, etc.) inherit from this POM
- A version change here affects every service in the platform simultaneously
- Node.js tooling (pnpm + Husky) for commit hooks and formatting only — not part of the Maven build
- Published to Maven Central via the `maven-central` profile

## What This Repo Contains

```
boot-parent-pom/
├── pom.xml          # The parent POM — all dependency and plugin version management
├── package.json     # Node tooling only (Husky, OxFmt, commitlint)
└── AGENTS.md
```

The `pom.xml` defines:
- `<properties>` — all version pins (`spring-boot.version`, `hibernate.version`, `testcontainers.version`, etc.)
- `<dependencyManagement>` — full dependency BOM imported by child services
- `<pluginManagement>` — Checkstyle, Surefire, JaCoCo, Compiler, Deploy, Javadoc plugin configs
- `<build>` — default plugin executions inherited by all children

## Execution Discipline

- A version bump here is a platform-wide change. Before bumping any dependency, check the Spring Boot / Spring Cloud compatibility matrix and the migration guide for the target version.
- Read the full release notes for any version you are bumping — do not assume patch releases are safe.
- After two identical build failures without new evidence, change approach — do not retry blindly.
- Never bump multiple major dependencies in the same commit. Isolate each change so regressions are traceable.
- Behavior proven and required gates green: finish. No speculative version bumps.

## Rules for Changing This POM

### Version bumps
- Always pin to an exact version — no ranges (`[1.0,)`, `LATEST`, `RELEASE`).
- Prefer bumps that are already part of a Spring Boot BOM (e.g., `spring-boot-dependencies`) over manual overrides — less drift.
- When overriding a version already managed by `spring-boot-dependencies`, add a comment explaining why.
- Check child service compatibility before merging: a major version bump to Hibernate, Liquibase, or Spring Security typically requires code changes in every service.

### Adding a new dependency to `<dependencyManagement>`
- Only add dependencies that are used by two or more child services. Single-service dependencies stay in that service's own POM.
- Specify `<scope>` explicitly when it is not `compile`.
- Never add a dependency that duplicates one already provided by an imported BOM without a documented reason.

### Plugin management
- Plugin version changes apply to every child build. Test against at least one service before committing.
- Checkstyle config version (`iqkv.checkstyle.version`) must stay in sync with `com.iqkv:checkstyle-config` releases.

## Security

- Keep credentials and tokens out of commits, logs, and shared text.
- Never add dependencies with known CVEs. Run `./mvnw dependency:analyze` and check OWASP reports before adding.
- Flag unusual artifact coordinates (groupId/artifactId) before adding — supply chain risk.
- Use exact versions; never use `-SNAPSHOT` versions in a published release.
- Never bypass `--no-verify` unless explicitly requested.

## AI Agent Development Guidelines

### Code generation principles

1. **No source code** — this repo contains only POM XML and tooling config
2. **One change per commit** — each dependency or plugin bump is its own commit with a clear rationale
3. **Compatibility first** — verify Spring Boot BOM compatibility before any Spring ecosystem bump
4. **Comment overrides** — any version that overrides a BOM-managed version needs an inline XML comment

### Approval workflow (MANDATORY)

Ask before applying. For any version change or new dependency:

```
1. ANALYZE  → identify what changed, what it affects, and compatibility risk
2. PRESENT  → show the proposed pom.xml diff and list affected child services
3. WAIT     → stop and wait for explicit approval
4. APPLY    → only after approval
5. VERIFY   → confirm ./mvnw verify passes on this repo
```

**Approval phrases:** "Yes", "Proceed", "Apply", "Do it", "Go ahead", "Looks good"

## Commit Standards

Format: `type(scope): subject`

- Subject: imperative, lowercase, no trailing period, ≤ 72 chars
- Types: `feat`, `fix`, `chore`, `ci`, `docs`, `revert`
- Scope: the dependency or plugin area being changed (e.g., `spring-boot`, `hibernate`, `checkstyle`, `testcontainers`, `jackson`, `deps`)
- For `fix`: describe the symptom and trigger, not the XML change
  - ✅ `fix(jackson): deserialization fails on nullable UUID fields with 2.17.x`
  - ❌ `fix(jackson): downgrade jackson to 2.16.2`

Examples:
- `chore(spring-boot): bump to 4.1.1`
- `chore(testcontainers): bump to 1.21.4`
- `feat(deps): add spring-modulith BOM to dependency management`
- `fix(checkstyle): pin checkstyle-config to 0.24.0 to match plugin version`
- `chore(pitest): bump mutation testing plugin to 1.30.0`

## Development Commands

```bash
# Validate POM structure and resolve dependency tree
./mvnw validate

# Full verify (runs effective POM checks, no source to compile)
./mvnw verify

# Display effective dependency versions
./mvnw dependency:display-dependency-updates

# Check for plugin updates
./mvnw versions:display-plugin-updates
```
