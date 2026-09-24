---
name: plan-before-action
description: Use when a task requires modifying code, configuration, files, or external systems.
---

# Plan before action

Before making changes:

1. Inspect the relevant project context using read-only operations.
2. Analyze the request, constraints, existing implementation, and likely impact.
3. Ask a clarifying question only when the answer would materially change the plan.
4. Present a concise action plan in the chat. Include:
   - the intended outcome;
   - the files or components likely to change;
   - the ordered implementation steps;
   - important assumptions, risks, or trade-offs.
5. Stop and wait for explicit user approval.

Do not treat the original request as approval of the plan.

If the user corrects or changes the plan:

1. Incorporate the feedback.
2. Present the revised plan.
3. Wait for explicit approval again.

After approval, implement the approved plan. If implementation reveals a material change in scope or approach, stop,
explain the discovery, present an updated plan, and request approval before continuing.

Do not require or create:

- a design specification;
- a separate plan document;
- test-driven development;
- mandatory test coverage;
- commits or pull requests;
- subagent workflows;
- additional review or approval stages.

Run tests or other verification only when the user requests them or when they are necessary to verify the requested
change. Keep verification proportional to the task.
