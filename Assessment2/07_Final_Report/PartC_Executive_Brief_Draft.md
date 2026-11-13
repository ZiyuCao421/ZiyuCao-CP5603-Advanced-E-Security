# Part C — Executive Brief: Security Priorities and Decisions

## Purpose

This brief consolidates the Assessment 2 evidence, issue analysis, risk register, ethics log and research record into decisions for Torridge University leadership. The evidence indicates material control weaknesses. It does **not** confirm that a compromise has occurred.

## Current risk position

Eight risks require managed treatment: four Critical (R01 network access, R03 student portal, R04 device management and R06 student information system) and four High (R02 legacy laboratory, R05 MFA resilience, R07 OAuth governance and R08 generative AI use). The priority is based on exposure, likely impact, affected services and the quality of available controls—not merely whether the issue is technical.

## Decisions requested

1. **Approve a 14-day remediation window** for the exposed student portal and default device-management settings. Remove unsafe service exposure; apply a hardened configuration; and retain test evidence.
2. **Require network-rule recertification and restricted administrative access.** Assign every exception an owner, business reason, expiry date and review date; narrow broad rules and limit SSH access.
3. **Fund student-information-system recovery protection.** Encrypt backups, retire TLS 1.0, establish key rotation, and test a documented restore.
4. **Set an MFA resilience standard.** Agree a monitored failover design and a time-limited, logged fallback process so service continuity does not silently weaken authentication.
5. **Centralise OAuth decisions.** Require least-privilege scopes, vendor review, accountable ownership and periodic re-authorisation for third-party integrations.
6. **Approve controlled generative-AI use.** Publish an approved-tool and data-classification rule, implement enterprise access where appropriate, and train staff and students on permitted use.
7. **Do not close actions on assurance alone.** Require acceptance evidence, a named owner, target date, residual-risk decision and review cadence for every treatment.

## Delivery roadmap

| Timing | Outcome | Risks addressed |
|---|---|---|
| 0–14 days | Portal and device-management exposure removed and tested | R03, R04 |
| 15–30 days | Network rules recertified; MFA, SIS backup and OAuth controls strengthened | R01, R05, R06, R07 |
| 31–45 days | Generative-AI rule, approved service path and awareness material operating | R08 |
| 46–60 days | Legacy laboratory access constrained, isolated and given a replacement decision | R02 |

## Accountability and assurance

Technology owners should provide implementation evidence; service owners should accept operational impact; and the security function should validate closure against the risk register. Evidence should include configuration records, test results, review records or restore tests—not a statement that work is complete. Critical risks require frequent leadership review until the residual risk is explicitly accepted or reduced.

## Ethical and operational balance

Treatments must protect student and staff information without creating unreasonable barriers to learning, research or accessibility. Legacy and temporary exceptions should therefore be limited, recorded, time-bound and reviewed. Security reporting must distinguish observed evidence, reasonable inference and unconfirmed compromise so leadership decisions remain honest, proportionate and defensible.

## Leadership endorsement

Endorse the prioritised roadmap, accountable owners and evidence-based closure criteria; require progress reporting against the stated dates; and escalate any decision to accept residual Critical risk.
