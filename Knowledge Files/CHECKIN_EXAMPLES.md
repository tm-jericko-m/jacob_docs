# Jacob Golden Checkin Examples

Use these examples as the golden dataset for output quality. Follow their structure, tone, conservatism, and handling of unclear data.

## Example 1: Full day with structured activities

Input:
```json
{
  "date": "2026-06-09",
  "activities": [
    {"source": "slack", "project": "intern-machines-2026", "hours": 2.5, "description": "Search for TM8 members and schedule 1:1 culture meetings"},
    {"source": "calendar", "project": "intern-machines-2026", "hours": 2.5, "description": "Check participant availability in calendar"},
    {"source": "calendar", "project": "intern-machines-2026", "hours": 2.0, "description": "Book 1:1 culture meetings"},
    {"source": "task", "project": "intern-machines-2026", "hours": 0.5, "description": "Rechecked and confirmed all accounts and access based on digital security master checklist"},
    {"source": "meeting", "project": "intern-machines-2026", "hours": 0.5, "description": "Consulted with intern manager"}
  ]
}
```

Expected output:
```text
checkin 2026-06-09
• 2.5 hrs #intern-machines-2026 Searched for TM8 members and scheduled 1:1 culture meetings
• 2.5 hrs #intern-machines-2026 Checked participant availability in calendar
• 2.0 hrs #intern-machines-2026 Booked 1:1 culture meetings
• 0.5 hrs #intern-machines-2026 Rechecked and confirmed accounts and access using the digital security master checklist
• 0.5 hrs #intern-machines-2026 Consulted with intern manager
```

## Example 2: Calendar-only day with culture meetings

Input:
```json
{
  "date": "2026-06-10",
  "activities": [
    {"source": "calendar", "project": "culture", "hours": 0.5, "description": "Marco Enrico / Juan Jericko 1:1 culture meeting"},
    {"source": "calendar", "project": "culture", "hours": 1.5, "description": "Stuart / Juan Jericko 1:1 culture meeting"},
    {"source": "calendar", "project": "culture", "hours": 0.5, "description": "Kait / Juan Jericko 1:1 culture meeting"},
    {"source": "calendar", "project": "intern-machines-2026", "hours": 5.5, "description": "Search for availability and book 1:1 culture meetings"}
  ]
}
```

Expected output:
```text
checkin 2026-06-10
• 0.5 hrs #culture Attended 1:1 culture meeting with Marco Enrico
• 1.5 hrs #culture Attended 1:1 culture meeting with Stuart
• 0.5 hrs #culture Attended 1:1 culture meeting with Kait
• 5.5 hrs #intern-machines-2026 Searched for availability and booked 1:1 culture meetings
```

## Example 3: Less than 8 confirmed hours

Input:
```json
{
  "date": "2026-06-11",
  "activities": [
    {"source": "calendar", "project": "intern-machines-2026", "hours": 2.0, "description": "Intern onboarding checklist review"},
    {"source": "slack", "project": "intern-machines-2026", "description": "Confirmed some access items but did not mention time spent"}
  ]
}
```

Expected output:
```text
checkin 2026-06-11
• 2.0 hrs #intern-machines-2026 Reviewed intern onboarding checklist and confirmed access items

Needs clarification:
- Confirm whether there was additional time spent on access confirmation beyond the 2.0 hr calendar block.
- The confirmed total is 2.0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 4: Slack and calendar duplicate should be merged

Input:
```json
{
  "date": "2026-06-12",
  "activities": [
    {"source": "calendar", "project": "intern-machines-2026", "hours": 2.0, "description": "#intern-machines-2026 Culture 1:1 scheduling"},
    {"source": "slack", "project": "intern-machines-2026", "description": "Booked the remaining culture 1:1 meetings and sent the invites"},
    {"source": "gmail", "project": "intern-machines-2026", "description": "Calendar invites sent to participants"}
  ]
}
```

Expected output:
```text
checkin 2026-06-12
• 2.0 hrs #intern-machines-2026 Scheduled and sent invites for culture 1:1 meetings

Needs clarification:
- The confirmed total is 2.0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 5: Slack activity without duration

Input:
```json
{
  "date": "2026-06-13",
  "activities": [
    {"source": "slack", "project": "jacob", "description": "Reviewed the Jacob prompt and suggested moving examples into a separate checkin examples file"}
  ]
}
```

Expected output:
```text
checkin 2026-06-13

Needs clarification:
- Confirm how much time was spent reviewing the Jacob prompt and separating examples into CHECKIN_EXAMPLES.md.
- The confirmed total is 0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 6: Calendar event with no project tag but clear mapping

Input:
```json
{
  "date": "2026-06-14",
  "activities": [
    {"source": "calendar", "title": "Jacob Custom GPT prompt refinement", "start": "2026-06-14T09:00:00+08:00", "end": "2026-06-14T11:30:00+08:00"},
    {"source": "user_note", "description": "Jacob work should use #jacob"}
  ]
}
```

Expected output:
```text
checkin 2026-06-14
• 2.5 hrs #jacob Refined the Jacob Custom GPT prompt

Needs clarification:
- The confirmed total is 2.5 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 7: Personal and excluded events should not count

Input:
```json
{
  "date": "2026-06-15",
  "activities": [
    {"source": "calendar", "title": "❇️ Lunch (via Clockwise)", "start": "2026-06-15T12:00:00+08:00", "end": "2026-06-15T13:00:00+08:00"},
    {"source": "calendar", "title": "#jacob Review prompt guardrails", "start": "2026-06-15T13:00:00+08:00", "end": "2026-06-15T15:00:00+08:00"},
    {"source": "calendar", "title": "TM Weekly Game Night", "start": "2026-06-15T18:00:00+08:00", "end": "2026-06-15T19:00:00+08:00"}
  ]
}
```

Expected output:
```text
checkin 2026-06-15
• 2.0 hrs #jacob Reviewed Jacob prompt guardrails

Needs clarification:
- The confirmed total is 2.0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 8: Tentative event without confirmation

Input:
```json
{
  "date": "2026-06-16",
  "activities": [
    {"source": "calendar", "project": "jacob", "hours": 1.0, "status": "tentative", "description": "Jacob backend sync discussion"},
    {"source": "slack", "project": "jacob", "description": "No related messages from the user"}
  ]
}
```

Expected output:
```text
checkin 2026-06-16

Needs clarification:
- Confirm whether the tentative Jacob backend sync discussion happened and whether it should count as 1.0 hr.
- The confirmed total is 0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 9: Declined event should be excluded

Input:
```json
{
  "date": "2026-06-17",
  "activities": [
    {"source": "calendar", "project": "culture", "hours": 1.0, "status": "declined", "description": "Culture sync"},
    {"source": "calendar", "project": "jacob", "hours": 3.0, "status": "accepted", "description": "Prompt and examples cleanup"}
  ]
}
```

Expected output:
```text
checkin 2026-06-17
• 3.0 hrs #jacob Cleaned up Jacob prompt and checkin examples

Needs clarification:
- The confirmed total is 3.0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 10: Multiple projects in one day

Input:
```json
{
  "date": "2026-06-18",
  "activities": [
    {"source": "calendar", "project": "jacob", "hours": 3.0, "description": "Update Jacob prompt structure"},
    {"source": "calendar", "project": "ai-101", "hours": 2.0, "description": "Review AI 101 notes on 4D framework"},
    {"source": "task", "project": "edward", "hours": 1.5, "description": "Check Edward repo calendar filtering logic"},
    {"source": "meeting", "project": "intern-machines-2026", "hours": 1.5, "description": "Coordinate intern onboarding follow-ups"}
  ]
}
```

Expected output:
```text
checkin 2026-06-18
• 3.0 hrs #jacob Updated Jacob prompt structure
• 2.0 hrs #ai-101 Reviewed AI 101 notes on the 4D framework
• 1.5 hrs #edward Checked Edward repo calendar filtering logic
• 1.5 hrs #intern-machines-2026 Coordinated intern onboarding follow-ups
```

## Example 11: Unclear project tag

Input:
```json
{
  "date": "2026-06-19",
  "activities": [
    {"source": "calendar", "hours": 1.5, "description": "Review draft rollout notes"},
    {"source": "slack", "description": "Discussed draft rollout notes but no project/channel context was included"}
  ]
}
```

Expected output:
```text
checkin 2026-06-19
• 1.5 hrs #uncategorized Reviewed draft rollout notes

Needs clarification:
- Confirm the correct project hashtag for the draft rollout notes.
- The confirmed total is 1.5 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 12: Overlapping calendar events

Input:
```json
{
  "date": "2026-06-20",
  "activities": [
    {"source": "calendar", "project": "jacob", "title": "#jacob Prompt cleanup", "start": "2026-06-20T09:00:00+08:00", "end": "2026-06-20T11:00:00+08:00"},
    {"source": "calendar", "project": "jacob", "title": "#jacob Checkin examples review", "start": "2026-06-20T10:30:00+08:00", "end": "2026-06-20T12:00:00+08:00"}
  ]
}
```

Expected output:
```text
checkin 2026-06-20
• 2.0 hrs #jacob Cleaned up Jacob prompt
• 1.5 hrs #jacob Reviewed checkin examples

Needs clarification:
- The calendar events overlap from 10:30 to 11:00. Confirm whether to count both events separately or adjust the total to avoid double-counting.
- The unadjusted confirmed total is 3.5 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 13: User correction overrides inferred data

Input:
```json
{
  "date": "2026-06-21",
  "activities": [
    {"source": "calendar", "project": "jacob", "hours": 2.0, "description": "Jacob prompt review"},
    {"source": "user_note", "description": "Actually this was for Edward migration, not Jacob"}
  ]
}
```

Expected output:
```text
checkin 2026-06-21
• 2.0 hrs #edward Reviewed prompt changes for Edward migration

Needs clarification:
- The confirmed total is 2.0 hrs. I need more source data or user confirmation to reach 8 hrs.
```

## Example 14: Full day after manual user-provided source data

Input:
```json
{
  "date": "2026-06-22",
  "activities": [
    {"source": "user_note", "project": "jacob", "hours": 2.0, "description": "Created cleaned Custom GPT instructions without examples"},
    {"source": "user_note", "project": "jacob", "hours": 2.0, "description": "Built checkin examples golden dataset"},
    {"source": "user_note", "project": "jacob", "hours": 1.0, "description": "Created project tag and non-work event reference files"},
    {"source": "user_note", "project": "ai-101", "hours": 1.5, "description": "Mapped AI 101 4D framework to Jacob guardrails"},
    {"source": "user_note", "project": "edward", "hours": 1.5, "description": "Compared Jacob behavior against Edward calendar checkin format"}
  ]
}
```

Expected output:
```text
checkin 2026-06-22
• 2.0 hrs #jacob Created cleaned Custom GPT instructions without embedded examples
• 2.0 hrs #jacob Built the checkin examples golden dataset
• 1.0 hrs #jacob Created project tag and non-work event reference files
• 1.5 hrs #ai-101 Mapped the AI 101 4D framework to Jacob guardrails
• 1.5 hrs #edward Compared Jacob behavior against Edward's calendar checkin format
```
