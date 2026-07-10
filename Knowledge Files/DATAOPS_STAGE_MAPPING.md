# DATAOPS Stage Mapping

This document maps observed work activity into the standardized DataOps TM8 SDLC stages and task categories.

When multiple mappings are possible, choose the one that best represents the primary work performed.

---

# Stage Overview

## Set Up

Purpose

Preparation work before investigation or implementation.

Typical tasks

- Devices + Environment Build
- Repository Setup
- Access Configuration
- Mandatory Client Training

Common wording

- setup
- laptop update
- patch
- onboarding
- repo
- repository
- clone
- VPN
- WSL
- environment
- access
- credentials
- configuration

---

## RCA

Purpose

Understanding the issue before implementation.

Tasks

- RCA
- Research
- Scoping

Common wording

- investigate
- investigation
- debugging
- debug
- research
- review
- explore
- clarify
- requirement review
- design
- scope
- timeline
- reproduce

---

## Fix

Purpose

Implementation or post-implementation work.

### Dev

Common wording

- fix
- bug
- coding
- implement
- resolution
- vulnerability
- update logic
- code change
- feature restoration

---

### QA

Common wording

- verify
- verification
- validation
- testing
- monitor
- monitoring
- UAT
- confirm
- check status

---

### Deploy

Common wording

- deploy
- deployment
- CAB
- CHG
- release
- prod deployment
- deployment prep
- rollout

---

### Documentation

Common wording

- documentation
- writeup
- report
- jira update
- post-mortem
- EOD update
- summary

---

### Sync

Common wording

- sync
- huddle
- working session
- alignment
- backlog discussion
- internal meeting
- standup

---

### Customer Call

Common wording

- client meeting
- external meeting
- customer call
- IT call
- stakeholder meeting
- production discussion

---

### Latency

Common wording

- waiting
- blocked
- pending
- approval
- CAB approval
- client response
- external dependency

---

# Resolution Rules

When multiple keywords appear:

Priority:

1. Explicit Jira stage
2. Developer wording
3. Golden dataset similarity
4. User clarification

---

Never output:

- multiple stages
- multiple task categories

Split work into separate checkins instead.

---

If classification confidence is low:

Ask the user.

Do not guess.