---
description: This instuction contains rules to follow when implementing java projects
---

# Java coding rules
1. All new classes must be placed in the "com.github.exadmin.${PROJECT_NAME}" package, where $PROJECT_NAME is a name of the project (or repository). Ask when unclear.
2. Use JDK 17+ language level.
3. All comments and messages in the source code must be written in English

# Logging
1. Do not use plain logging to console until explicity asked
2. Use slf4j + log4j for logging with default configuration to print logs into console

# Other
1. Note that user may modify sources you've touched/read in parallel. Re-read sources each time you need them.
2. Place all static utility methods into separate classes like (StrUtils for strings operating, FileUtils for files operating, DateUtils for date-time operating and so on).
3. Each public method and class must have clear JavaDocs description. If file was modified by you - then verify JavaDocs description of corresponding method you've touched.

# Security best practies
1. If project requires program secret-arguments (tokens, passwords, API Keys) - then all such arguments must be requested via external Java-properties file. And the path to such file must be the only program argument.

