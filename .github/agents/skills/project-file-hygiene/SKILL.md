---
name: project-file-hygiene
description: Ensures clean project structures by separating application source code, documentation and AI agent execution artifacts. Use whenever creating or modifying software projects.
---

# Project File Hygiene Skill

## Objective

Maintain clean, production-ready application repositories.

AI agent instructions, execution logs, temporary reports and planning documents must not pollute application source code.

## 1. Application project files

For a Spring Boot Maven application, allow:

- pom.xml
- README.md
- .gitignore
- src/main/java/
- src/main/resources/
- src/test/java/

Other application files may be added when required by the project.

## 2. Prohibited unnecessary files

Do not automatically create these files inside the application:

- plan.md
- progress.md
- summary.md
- summary.template.md
- execution-log.md
- agent-notes.md
- task-history.md

Create them only when explicitly requested by the user.

## 3. Agent configuration separation

Keep AI agent configuration outside generated application folders.

Recommended locations:

.github/agents/
.github/skills/

Never create agent configuration files inside the generated Spring Boot project.

## 4. Execution artifacts

Do not store agent execution artifacts in the application repository.

If execution reports are required, use a separate workspace directory:

.agent-work/

Example:

.agent-work/
    springboot-project-creator/
        reports/
        logs/

Do not create this directory unless execution artifacts are actually needed.

## 5. Git protection

Before Git initialization or commit:

1. Inspect project structure.
2. Identify unnecessary generated files.
3. Exclude temporary files and execution logs.
4. Check .gitignore.
5. Review git status.
6. Commit only relevant application files.

Never delete existing user files without permission.

## 6. Final validation

Before completing any project generation:

- Verify application source structure.
- Verify pom.xml exists.
- Verify README.md exists.
- Verify no unnecessary agent-generated Markdown files exist.
- Verify no agent execution logs exist in the application folder.
- Verify Git contains only relevant project files.

## 7. Important rule

The generated project must remain independent of the AI agent.

A developer should be able to clone the repository, import it into IntelliJ IDEA and build it using Maven without needing any AI agent configuration or execution artifacts.
