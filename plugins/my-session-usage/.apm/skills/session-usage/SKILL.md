---
name: session-usage
description: Report ccusage statistics for the current agent session when the user explicitly asks for session costs, token usage, or a usage signature. Do not add statistics to ordinary answers.
---

# Session usage

Use the installed ccusage utility only when the user requests usage statistics. Collect a fresh snapshot near the end of the requested work and append its signature as the very last line of the final answer, separated by a blank line. If only a signature is requested, return only the signature.

## Collect the current session

- Identify the current runtime and its exact session ID from runtime-provided metadata. For Codex, use CODEX_SESSION_ID, falling back to CODEX_THREAD_ID. If both exist and disagree, resolve the discrepancy before proceeding.
- For Codex in PowerShell, run `ccusage codex session --id $env:CODEX_SESSION_ID --json --offline` (substitute the verified thread ID if needed). On other shells, use the corresponding environment-variable syntax.
- For another runtime, inspect `ccusage <runtime> session --help` and use its supported exact-session filter. Do not assume all adapters use the same flags or JSON schema.
- Verify that the returned record belongs to the exact requested session; Codex may return a path containing its ID. Never substitute the latest session, project totals, daily totals, or all-session totals.
- If ccusage is missing, the session is unknown, the command fails, or no matching record exists, explain the limitation briefly. Do not install utilities, invent statistics, or turn missing data into zero.
- Prefer offline cached pricing. If unavailable, disclose that cost is unavailable; omit usd. Do not silently change pricing modes or modify ccusage configuration.

## Format the signature

Use the actual main-agent model identifier from runtime metadata or the verified session data. A multi-model report does not establish which model is the main agent. Include reasoning effort only when runtime metadata provides it. Omit unknown fields, including model and effort; never use placeholders.

Append raw Markdown/HTML, without a code fence or backticks:

<sub>🤖 MODEL EFFORT in=12k cached=40k out=3k usd=0.083</sub>

The values above are illustrative. Normalize adapter-specific fields before formatting:

- `in`: input tokens excluding cache reads, including cache writes. For the Codex ccusage JSON schema with separate inputTokens/cacheReadTokens, use inputTokens; do not subtract cacheReadTokens again. For Anthropic data, include cache-creation input once. Inspect other schemas rather than assuming identical semantics.
- `cached`: input tokens read from cache (Codex: cacheReadTokens).
- `out`: output tokens including reasoning. Codex outputTokens already includes reasoning; do not add reasoningOutputTokens again.
- `usd`: totalCost, rounded to two significant digits. This is an estimated API-equivalent cost from ccusage pricing, not necessarily an actual subscription charge. If explanations are allowed, state that distinction before the signature.

Use k for thousands of tokens, with reasonable precision (29476 becomes 29.5k). Preserve real zero values; omit unavailable values. Use session totals, not per-response deltas. Do not sum session totals and model breakdowns together. Include subagent usage only if the adapter demonstrably includes it; do not claim coverage otherwise.

The snapshot may exclude the final answer currently being generated. When providing an explanation, mention this briefly before the signature. Never call ccusage again merely to account for the reporting call itself.
