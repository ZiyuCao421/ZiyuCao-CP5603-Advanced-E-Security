# Risk Prioritisation Worksheet

## Status and use

This is a **planning worksheet**, not a final assessment conclusion. The draft calibrations below must be checked against the original private evidence, approved risk criteria, and the marking rubric before they are used in a report.

## Scoring method

Use a 5 × 5 matrix: inherent rating = likelihood × impact.

| Likelihood | Score | Impact | Score |
|---|---:|---|---:|
| Rare / Unlikely / Possible / Likely / Almost certain | 1–5 | Insignificant / Minor / Moderate / Major / Severe | 1–5 |

1–4 Low · 5–9 Moderate · 10–16 High · 17–25 Critical.

## Draft candidate-risk calibration

| ID | Risk statement | Evidence themes to validate | Likelihood | Impact | Score | Draft priority | Immediate validation required |
|---|---|---|---:|---:|---:|---|---|
| R01 | Broad or inconsistent network access controls enable unauthorised access or lateral movement. | Firewall governance, exception handling, actual access records | 4 | 5 | 20 | Critical | Confirm active rule order, approved source scope, and compensating controls. |
| R02 | Weak SIS protection across backup, transport, key management, and change processes compromises confidentiality, integrity, or availability. | Cryptography assessment, change management, system dependencies | 3 | 5 | 15 | High | Confirm data classification, backup protection, protocol status, and recovery testing. |
| R03 | Public portal weaknesses and uninvestigated attack indicators lead to remote exploitation or service compromise. | Penetration testing, web and IDS indicators, patch state | 3 | 5 | 15 | High | Confirm remediation status, exposure, detection coverage, and incident outcome. |
| R04 | Weak management-interface controls expose network devices to unauthorised configuration or reconnaissance. | SNMP findings, monitoring alerts, credential controls | 4 | 4 | 16 | High | Confirm credential replacement, management-network restriction, and alert investigation. |
| R05 | Third-party MFA dependence impairs secure access or continuity during provider degradation. | Incident report, authentication patterns, policy, user feedback | 3 | 4 | 12 | High | Confirm service obligations, fallback governance, and MFA coverage. |
| R06 | Unreviewed third-party integrations and GenAI use create data-handling, privacy, or access-governance risk. | Plugin deployment, staff feedback, GenAI governance | 3 | 4 | 12 | High | Confirm OAuth scopes, vendor review, data classification, and approved-use controls. |

## Control-evaluation prompts

For each selected risk, distinguish implemented controls from designed or approved controls, then record gaps, treatment choice, accountable owner, target date, trade-offs, and residual rating.

## Next work items

- [ ] Validate the draft ratings against the private evidence and marking criteria.
- [ ] Select the five final risks.
- [ ] Complete control-effectiveness and residual-risk ratings in `Risk_Register_Template.csv`.
- [ ] Turn priority treatments into a 12-month roadmap in `06_Innovation_Design/`.
