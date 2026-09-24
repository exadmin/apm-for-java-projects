---
description: This instruction contains rules to follow when implementing Java projects
applyTo: "**/*.java"
---

# Java coding rules
1. All new classes must be placed under the `com.github.exadmin.${PROJECT_NAME}` package (sub-packages are allowed to be created and used), where `${PROJECT_NAME}` is the name of the project (or repository). Ask when unclear.
2. Use JDK 17+ language level.
4. Don't use internal (embedded) classes or records. All such entities must be placed into personal java files (with public or package protected access level).
5. Prefer using following sub-packages names
   6. `utils` for auxiliary classes with static methods
   7. `model` for POJO, DTO and other public model classes, including records.
   8. `api` for Interfaces, Abstract classes and other public API.
   9. `impl` for implementation classes

# Logging
1. Do not use plain logging to console unless explicitly asked.
2. Use SLF4J + Log4j for logging with default configuration to print logs into console.
3. System.out.println() is allowed only for printing application usage tooltips or during program arguments checking steps.

# Code Formatting
1. Place all static utility methods into separate classes like `StrUtils` for string operations, `FileUtils` for file operations, `DateUtils` for date-time operations, and so on.
2. Each public method and class must have clear JavaDocs description. If a file was modified by you, then verify the JavaDocs description of the corresponding method you've touched.
3. Do not perform import optimizations or unused imports search.
4. All comments and messages in the source code must be written in English.
5. Code lines inside same method must be grouped logically into blocks, each block is started with single-line comment, an empty line goes before the comment. No empty line right after '{' char. See example: 
```java
public void someMethod(String arg) {
    // Check arg has allowed value
    if (arg == null || !arg.equals("one") || !arg.equals("two")) {
        throw new ...
    }
    
    // Setup connection to database
    Connection conn = ...
    
    // Query database using arg as bind value
    ...
}
```

# Security best practices
1. If the project requires program secret arguments (tokens, passwords, API keys), then all such arguments must be requested via an external Java properties file, and the path to such file must be one of program arguments.

# Other
1. Do not hard code values right in the code. Use public/private final constant values or enums.