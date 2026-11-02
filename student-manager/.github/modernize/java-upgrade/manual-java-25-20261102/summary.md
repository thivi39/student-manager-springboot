# Java Upgrade Summary: student-manager

- **Target Java**: 25.0.5 LTS
- **Completed**: 2026-11-02
- **Build tool**: Maven Wrapper 3.10.0
- **Framework**: Spring Boot 4.1.2

## Files Changed

- `pom.xml`: changed `<java.version>` from `21` to `25`.
- `.github/modernize/java-upgrade/manual-java-25-20261102/plan.md`: upgrade plan.
- `.github/modernize/java-upgrade/manual-java-25-20261102/progress.md`: execution record.
- `.github/modernize/java-upgrade/manual-java-25-20261102/summary.md`: this summary.

## Validation

- Baseline on Java 27: `mvnw.cmd -q clean test` passed, 1/1 tests.
- Java 25 compilation: `mvnw.cmd -q clean test-compile` passed.
- Java 25 tests and verification: `mvnw.cmd -q clean verify -Djacoco.skip=false` passed, 1/1 tests.
- Spring Boot context loaded successfully on Java 25.

## Key Risks and Blockers

- Mockito/Byte Buddy reports a non-fatal dynamic-agent warning on Java 25. Tests pass; no behavioral failure was observed.
- Automated CVE validation was blocked because the modernization backend returned `agent-host-copilotcli:auto` model unavailable. Direct dependency versions were inspected, and no speculative dependency changes were made.
- The project directory is not a Git repository; no branch or commits were created.
