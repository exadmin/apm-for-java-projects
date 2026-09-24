# apm-for-java-projects

Personal APM marketplace for Java development and planning workflows.

## Available plugins

- `my-java-dev`: Git and Java development instructions.
- `my-super-powers`: Requires an approved action plan before making changes.

## Install a plugin

Register the marketplace once:

```shell
apm marketplace add exadmin/apm-for-java-projects
```

Install either plugin in a project:

```shell
apm install my-java-dev@apm-for-java-projects --target codex
```

```shell
apm install my-super-powers@apm-for-java-projects --target codex
```

Compile the installed primitives:

```shell
apm compile --target codex
```
