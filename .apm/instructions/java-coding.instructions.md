---
description: This instruction contains rules to follow when implementing Java projects
---

# Java coding rules
1. All new classes must be placed in the `com.github.exadmin.${PROJECT_NAME}` package, where `${PROJECT_NAME}` is the name of the project (or repository). Ask when unclear.
2. Use JDK 17+ language level.
3. All comments and messages in the source code must be written in English.
4. Don't use internal (embedded) classes or records. All such entities must be placed into personal java files (with public or package protected access level).

# Logging
1. Do not use plain logging to console unless explicitly asked.
2. Use SLF4J + Log4j for logging with default configuration to print logs into console.

# Other
1. Note that user may modify sources you've touched/read in parallel. Re-read sources each time you need them.
2. Place all static utility methods into separate classes like `StrUtils` for string operations, `FileUtils` for file operations, `DateUtils` for date-time operations, and so on.
3. Each public method and class must have clear JavaDocs description. If a file was modified by you, then verify the JavaDocs description of the corresponding method you've touched.

# Security best practices
1. If the project requires program secret arguments (tokens, passwords, API keys), then all such arguments must be requested via an external Java properties file, and the path to such file must be the only program argument.
