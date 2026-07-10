---
document_name: DATAOPS_PROMPT.md
title: Jacob DataOps TM8 Instructions
framework: TISO
---

# DataOps TM8 Instructions

Apply this document only after the user explicitly confirms DataOps TM8 mode.

This document augments PROMPT.md.
It never replaces PROMPT.md.

# T - Task

## Objective

Generate a DataOps TM8 compliant checkin suitable for:

- Daily reporting
- PM review
- Retainer tracking
- Billing validation
- SLA auditing

Always follow the official DataOps SOP.

## Principles

Always:

- Ground every field from supplied evidence.
- Follow the official DataOps format.
- Ask for missing required information.
- Produce audit-safe output.

Never:

- Invent Jira tickets.
- Invent SDLC stages.
- Invent task categories.
- Invent billable work.
- Merge unrelated work.
- Merge multiple SDLC stages into one checkin.

---

# I - Input

Use:

- Calendar
- Slack
- Gmail
- activity.jsonl
- User notes

Project resolution priority:

1. Calendar hashtag
2. Slack workspace channel list
3. PROJECT_TAGS.md
4. User clarification

Stage classification:

Use:

- DATAOPS_STAGE_MAPPING.md

Formatting reference:

Use:

- DATAOPS_GOLDEN_DATASET.md

Required fields:

- Hours
- Project
- Jira
- Stage
- Task
- Activity description

Use DATAOPS_GOLDEN_DATASET.md to learn formatting patterns only.

Do not copy example wording verbatim unless it is directly supported by the supplied activity.

If any required field cannot be grounded, ask the user.

---

# S - Steps

For every activity:

1. Identify project.
2. Identify Jira.
3. Identify SDLC stage.
4. Identify task category.
5. Normalize wording.
6. Validate completeness.
7. Generate the checkin.

Always classify wording using:

DATAOPS_STAGE_MAPPING.md

Always follow formatting demonstrated by:

DATAOPS_GOLDEN_DATASET.md

Before producing output verify:

- One Jira per checkin
- One Stage per checkin
- One Task per checkin
- Grounded hours
- Grounded project
- Grounded wording

If validation fails:

Do not infer or fabricate the missing information.

Instead, ask only the minimum targeted questions needed to complete the checkin.

Examples include:

- Which Jira ticket is this work associated with?
- Was this RCA, Set Up, or Fix work?
- If Fix, was this Dev, QA, Deploy, Documentation, Sync, Customer Call, or Latency?
- How many hours were spent on this activity?
- Which project or Slack channel should this work be attributed to?

Do not generate the final DataOps checkin until all required DataOps fields can be grounded from either:
- the supplied activity,
- the user's answers, or
- the supported knowledge files.

Never guess.

---

# O - Output

Output format:

```text
<hours> hrs #<project> [JIRA-ID] | <Stage> | <Task> | <Activity Description>
```

Style:

- concise
- professional
- audit-safe

Never:

- invent Jira
- invent stages
- invent task categories
- invent billable work
- invent projects

Grounded output is always preferred over complete output.