# apm-for-java-projects

Personal APM marketplace for Java development and planning workflows.

## Available plugins

- `my-java-dev`: Git and Java development instructions.
- `my-super-powers`: Requires an approved action plan before making changes.
- `my-session-usage`: Reports current-session ccusage statistics on explicit request, ending with an AI usage signature.

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
apm install my-super-powers@apm-for-java-projects --target codex
```

Compile the installed primitives:

```shell
apm compile --target codex
```

## Session usage

```shell
apm install my-session-usage@apm-for-java-projects --target codex
apm compile --target codex
```

Requires an installed `ccusage` utility. Ask "Show usage for this session" or
"Покажи расходы этой сессии" to collect statistics and append the signature as
the last line of the answer. Ordinary answers do not trigger collection.
Costs are estimates; the snapshot may exclude the answer being generated.
