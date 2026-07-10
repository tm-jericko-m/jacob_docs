# DataOps Golden Dataset

The following examples demonstrate the expected transformation from observed developer activity into compliant DataOps TM8 checkins.

---

## Example 1 — RCA / Scoping

### Observed Activity

- Calendar: "BAPR-31 Investigation"
- Slack:
  - Discussed SQL timeout
  - Reviewed deployment logs
  - Asked for production access
- Gmail:
  - CAB approval request

### Expected Output

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-31] | RCA | Scoping | Reviewed deployment logs and investigated SQL timeout.

---

## Example 2 — RCA / Research

### Observed Activity

- Read Databricks documentation
- Investigated cryptography vulnerability
- No code changes yet

### Expected Output

1 hr #sd-bpi-aia-pia-pilot [BAPR-52] | RCA | Research | Researched cryptography vulnerability and reviewed Databricks documentation.

---

## Example 3 — Setup

### Observed Activity

- Updated laptop
- Repository setup
- Installed dependencies
- Configured VPN

### Expected Output

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-61] | Set Up | Devices + Environment Build | Completed repository setup, dependency installation and VPN configuration.

---

## Example 4 — Fix / Dev

### Observed Activity

- Modified ETL join
- Fixed duplicate records
- Updated transformation logic

### Expected Output

2 hrs #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | Dev | Fixed duplicate records by updating ETL transformation logic.

---

## Example 5 — Fix / QA

### Observed Activity

- UAT verification
- Monitoring deployment
- Confirmed issue resolved

### Expected Output

1 hr #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | QA | Verified deployment through UAT and confirmed issue resolution.

---

## Example 6 — Fix / Deploy

### Observed Activity

- CAB approval
- PROD deployment
- Deployment validation

### Expected Output

1 hr #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | Deploy | Completed production deployment following CAB approval.

---

## Example 7 — Fix / Documentation

### Observed Activity

- Updated Jira
- Wrote post-mortem
- Sent completion email

### Expected Output

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | Documentation | Updated Jira ticket and completed post-mortem documentation.

---

## Example 8 — Fix / Sync

### Observed Activity

- Internal troubleshooting session
- Working session with team
- Backlog discussion

### Expected Output

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | Sync | Internal troubleshooting session to align implementation approach.

---

## Example 9 — Fix / Customer Call

### Observed Activity

- Client deployment meeting
- Production discussion
- Clarified deployment schedule

### Expected Output

1 hr #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | Customer Call | Discussed production deployment timeline with client.

---

## Example 10 — Fix / Latency

### Observed Activity

- Waiting for CAB approval
- Blocked by client response

### Expected Output

0.25 hr #sd-bpi-aia-pia-pilot [BAPR-12] | Fix | Latency | Waiting for CAB approval before deployment.

---

## Example 11 — Multi-stage work

### Observed Activity

- Morning investigation
- Afternoon code fix
- Evening deployment verification

### Expected Output

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-78] | RCA | Research | Investigated deployment issue.

1 hr #sd-bpi-aia-pia-pilot [BAPR-78] | Fix | Dev | Updated deployment configuration.

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-78] | Fix | QA | Verified deployment after configuration update.

---

## Example 12 — Documentation + Sync separation

### Observed Activity

- Internal sync
- Jira update

### Expected Output

0.5 hrs #sd-bpi-aia-pia-pilot [BAPR-90] | Fix | Sync | Internal alignment regarding implementation.

0.25 hr #sd-bpi-aia-pia-pilot [BAPR-90] | Fix | Documentation | Updated Jira ticket after alignment.