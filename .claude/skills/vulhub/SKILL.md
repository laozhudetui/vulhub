```markdown
# vulhub Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the **vulhub** repository, a collection of pre-built vulnerable environments for CVE and exploit research. You'll learn the repository's coding conventions, how to add new environments, update documentation, and follow established workflows for consistent, high-quality contributions.

## Coding Conventions

- **Language:** Java (with supporting scripts and Dockerfiles)
- **Framework:** None detected (environments are Docker-based)
- **File Naming:** 
  - Use **PascalCase** for Java files (e.g., `VulnerableApp.java`)
  - Use lowercase with hyphens or underscores for scripts and Docker-related files (e.g., `docker-entrypoint.sh`, `001_schema.sql`)
- **Import Style:** Relative imports in Java
  ```java
  import mypackage.utils.Helper;
  ```
- **Export Style:** Named exports in Java
  ```java
  public class VulnerableApp { ... }
  ```
- **Directory Structure:**
  - Each vulnerable environment is under `{software}/{CVE}/`
  - Base Dockerfiles are under `base/{software}/{version}/Dockerfile`
  - Documentation: `README.md` (English), `README.zh-cn.md` (Chinese)
  - Proof-of-concept and exploit scripts: `poc.py`, `exploit.py`
  - Supporting files: images (`.png`), SQL scripts, entrypoint scripts

**Example Directory:**
```
tomcat/CVE-2017-12615/
  ├── README.md
  ├── README.zh-cn.md
  ├── docker-compose.yml
  ├── poc.py
  ├── exploit.py
  ├── 1.png
  ├── database/
  │   └── 001_schema.sql
  └── docker-entrypoint.sh
```

## Workflows

### Add New CVE Environment
**Trigger:** When adding a new vulnerable environment for a specific CVE or exploit scenario  
**Command:** `/new-cve-env`

1. Create or update a base Dockerfile in `base/{software}/{version}/Dockerfile`.
2. Add a new directory `{software}/{CVE}/` for the environment.
3. Include the following files as needed:
    - `README.md` (English documentation)
    - `README.zh-cn.md` (Chinese translation)
    - `docker-compose.yml`
    - `poc.py` or `exploit.py`
    - Images (`*.png`) for documentation
    - Supporting scripts (e.g., `docker-entrypoint.sh`, `database/001_schema.sql`)
4. Commit all files together with a descriptive message.

**Example:**
```
base/tomcat/8.5.15/Dockerfile
tomcat/CVE-2017-12615/README.md
tomcat/CVE-2017-12615/README.zh-cn.md
tomcat/CVE-2017-12615/docker-compose.yml
tomcat/CVE-2017-12615/poc.py
tomcat/CVE-2017-12615/1.png
tomcat/CVE-2017-12615/docker-entrypoint.sh
```

---

### Merge Feature Pull Request
**Trigger:** When merging a pull request that adds a new CVE environment or significant feature  
**Command:** `/merge-feature-pr`

1. Review and merge the pull request.
2. Ensure all new or changed files from the feature branch are included in the main branch in a single commit.

---

### Add or Update README Translation
**Trigger:** When providing or updating a Chinese translation for documentation  
**Command:** `/add-readme-translation`

1. Create or update `README.zh-cn.md` in the relevant CVE directory.
2. Optionally update `README.md` if there are improvements or corrections.

---

### Improve or Update Existing Manual
**Trigger:** When clarifying, correcting, or expanding documentation for an existing environment  
**Command:** `/improve-manual`

1. Edit `README.md` and/or `README.zh-cn.md` in the relevant CVE directory.
2. Optionally update or add images (`*.png`) or scripts.

---

## Testing Patterns

- **Testing Framework:** Unknown
- **Test File Pattern:** Files matching `*.test.*`
- **Testing Approach:** If you add Java code or scripts, include test files named like `VulnerableApp.test.java` or `exploit.test.py` in the same directory or a `tests/` subdirectory.

**Example:**
```
tomcat/CVE-2017-12615/exploit.test.py
```

## Commands

| Command              | Purpose                                                        |
|----------------------|----------------------------------------------------------------|
| /new-cve-env         | Add a new vulnerable environment for a CVE or exploit scenario |
| /merge-feature-pr    | Merge a feature pull request into the main branch              |
| /add-readme-translation | Add or update a Chinese translation for documentation       |
| /improve-manual      | Improve or update documentation for an existing environment    |
```
