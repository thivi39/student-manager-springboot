# Upgrade Plan: student-manager (manual-java-25-20261102)

- **Generated**: 2026-11-02 22:39 +05:30
- **HEAD Branch**: N/A (not a Git repository)
- **HEAD Commit ID**: N/A

## Available Tools

**JDKs**
- JDK 27.0.1.0.3: `C:\Program Files\Java\jdk-27.0.1.0.3` (baseline runtime)
- JDK 25.0.5+8: `C:\Users\thivi\.jdk\jdk-25.0.5+8` (target runtime)

**Build Tools**
- Maven Wrapper 3.10.0: `mvnw.cmd` (compatible with Java 25)

## Guidelines

> Note: You can add any specific guidelines or constraints for the upgrade process here if needed, bullet points are preferred.

- Preserve unrelated user changes.
- Execute the upgrade end-to-end in auto-execution mode.

## Options

- Working branch: N/A (not a Git repository)
- Run tests before and after the upgrade: true

## Upgrade Goals

- Java 25 (latest available LTS as of 2026-11-02)

## Technology Stack

| Technology/Dependency | Current | Min Compatible Version | Why Incompatible |
|---|---:|---:|---|
| Java | 21 | 25 | User requested runtime target |
| Spring Boot | 4.1.2 | 4.1.2 | Already compatible with Java 25 |
| Maven Wrapper | 3.10.0 | 3.9+ | Already compatible |
| H2 | BOM-managed 2.4.240 | 2.4.240 | No upgrade required |
| Hibernate ORM | BOM-managed 7.4.13.Final | 7.x | Spring Boot 4.1.2 manages a compatible version |

## Derived Upgrades

- Set the Maven `java.version` property to `25`; Spring Boot 4.1.2 already supports the target runtime.
- No framework, namespace, Kotlin, wrapper, or source rewrite is required.

## Impact Analysis

### Dependency Changes

| File | Dependency | Current | Action | Target | Reason |
|---|---|---:|---|---:|---|
| `pom.xml` | `java.version` property | 21 | upgrade | 25 | Compile and package for the requested LTS runtime |

### Source Code Changes

No source changes identified. The application uses standard Spring Boot APIs and has no JDK-internal imports or reflective access requiring migration.

### Configuration Changes

No application configuration changes identified.

### CI/CD Changes

No CI/CD files are present.

### Risks & Warnings

- Java 25 may expose stricter runtime-agent warnings in Mockito; baseline already reports a dynamic-agent warning, but tests pass. No behavior change is required for this upgrade.
- This directory is not a Git repository, so version-control checkpoints and commits are unavailable.

## Upgrade Steps

- Step 1: Setup Environment
  - **Rationale**: Select/install the target JDK and verify Maven.
  - **Changes to Make**: Use JDK 25.0.5+8 and Maven Wrapper 3.10.0.
  - **Verification**: `java -version` and `mvnw.cmd -version`.

- Step 2: Setup Baseline
  - **Rationale**: Establish pre-upgrade compilation and test results.
  - **Changes to Make**: None.
  - **Verification**: `mvnw.cmd -q clean test` on JDK 27. Baseline expected: compile and 1 test pass.

- Step 3: Upgrade Java Runtime Target
  - **Rationale**: Change only the Maven Java target; dependencies are already compatible.
  - **Changes to Make**: Apply the Dependency Changes table.
  - **Verification**: `mvnw.cmd -q clean test-compile` on JDK 25.

- Step 4: Final Validation
  - **Rationale**: Prove the target runtime compiles and all tests pass.
  - **Changes to Make**: Resolve any Java-25-specific compile or test failures.
  - **Verification**: `mvnw.cmd -q clean test` on JDK 25; expected 1/1 tests passed.

- Step 5: CVE Validation & Fix
  - **Rationale**: Check resolved direct dependency versions for known vulnerabilities.
  - **Changes to Make**: Upgrade only vulnerable dependencies if reported.
  - **Verification**: Dependency scan and final compilation.

- Step 6: Final Summary
  - **Rationale**: Record changed files, validation, coverage, and limitations.
  - **Changes to Make**: Write `progress.md` and `summary.md`.
  - **Verification**: Confirm all required records exist and no upgrade TODOs remain.
