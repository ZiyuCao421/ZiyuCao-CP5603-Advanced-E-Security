# Part C — Security Brief for University Leaders

## What we found

We did not find proof that someone has broken into University systems. We did find weaknesses that could make important services and information easier to disrupt, misuse or expose. Eight risks need action: four are urgent and four are high priority.

## Plain-language priorities

- Some network rules allow access more widely than necessary. Each rule should have a named owner, a reason, an end date and a regular check.
- The student portal needs prompt hardening because testing traffic was observed. Exposure must be removed and the fix tested.
- Some network equipment still uses a default management setting. **Device management** means the way administrators control network equipment; default settings are widely known and should not remain in use.
- Student-information backups need better protection. A **backup** is a copy used to recover a system. It should be encrypted, restored in a test, and sent using current secure connections. **TLS 1.0** is an older method for protecting information while it travels across a network.
- The University needs a reliable backup plan for MFA. **MFA (multi-factor authentication)** is the extra sign-in check, such as a phone prompt, used alongside a password. Any emergency alternative must be short-lived and recorded.
- External learning services need tighter access approval. **OAuth** is a method that lets one service use limited access to another service on a person’s behalf. It should only receive the access it needs.
- Generative-AI use needs clear boundaries. Staff and students need to know which tools are approved and what information must never be entered into them.

## Decisions requested

1. Approve a 14-day action window for the student portal and network-device settings.
2. Require network-rule review, safer backups, MFA resilience and external-service access controls within 30 days.
3. Approve a University-wide generative-AI use rule, approved tools and short awareness material within 45 days.
4. Limit and isolate the older laboratory environment within 60 days while a replacement decision is made.

## How leaders will know work is complete

Every action needs a responsible owner, target date, proof of the change and a next review date. Proof can include a configuration record, a test result, a signed review or a successful recovery test. Work is not complete simply because a team says that it is.

## The leadership role

Approve the timetable and accountable owners; receive short progress reports; and decide explicitly if any urgent risk must remain. This protects learning, research and personal information while keeping security controls fair and practical.
