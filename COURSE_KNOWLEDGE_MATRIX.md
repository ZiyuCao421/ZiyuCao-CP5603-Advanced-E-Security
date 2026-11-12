# Course Knowledge Matrix — CP5603 Advanced E-Security

## Purpose

This is a concise, original working matrix that connects course concepts to analysis and report writing in this repository. It is not a copy of lecture slides or other course materials.

## How to use it

For each report claim, start with the case evidence. Use the matching course lens to explain why the issue matters, how it should be classified, what a proportionate control looks like, and what remains to be verified.

| Course area | Core lens | Case connections | Report writing rule |
| --- | --- | --- | --- |
| Security fundamentals | Asset; threat; vulnerability; control; impact; risk | All Evidence Pack items and risks R01-R08 | Separate observed fact from inference. A risk is the plausible consequence of a threat exploiting a weakness, not a synonym for the weakness. |
| Endpoint and web security | Attack surface; patching; secure configuration; input handling; monitoring | Portal findings E01; E06; E07 and R03 | Treat suspicious requests and IDS alerts as indicators requiring correlation, not proof of a successful compromise. |
| Cryptography | Confidentiality; integrity; availability; encryption at rest and in transit; key lifecycle | SIS encryption and backup issues E11; SIS change record E12; R06 | Do not describe AES-256 database encryption as complete protection when backups, transport security, keys or recovery controls are weak. |
| Network security | Defence in depth; segmentation; least privilege; secure management; firewall and IDS/IPS roles | Network overview E03; firewall logs E04; rules E05; SNMP E01; E02; E06; lab exception E13; R01; R02; R04 | Explain how overlapping controls should work together. Validate firewall rule order, hit counts and compensating controls before drawing final conclusions. |
| Authentication | Authentication factors; MFA; credential attacks; resilient access | MFA incident E08; authentication logs E09; policy E10; staff feedback E15; R05 | Analyse MFA as both a security control and a service requiring safe fallback, logging, user communication and resilience testing. |
| Enterprise security | Governance; ownership; third-party assurance; change control; policy implementation | SIS change record E12; LMS OAuth plugin E14; GenAI evidence E15-E16; R06-R08 | Link technical treatment to approval, ownership, review, supplier scope, data classification and practical user guidance. |
| Incident preparation and response | Prepare; detect; triage; investigate; contain; recover; learn | IDS, firewall, web, SNMP and authentication records E02; E04; E06-E09 | Preserve evidence and correlate sources. Distinguish an alert, an investigated incident and a confirmed impact. Include recovery and rollback in recommendations. |
| Professional ethics | Honesty; competence; respect; public interest; accountability | All findings; especially R03-R08 | Report uncertainty honestly, protect student and staff information, escalate outside personal competence, and choose proportionate controls. |

## Reusable analysis chain

1. Identify the asset or process.
2. Record the evidence-supported fact and its limitation.
3. Classify the issue: threat, vulnerability, control failure or process issue.
4. State the realistic threat event and potential impact.
5. Prioritise using likelihood, impact, exposure and evidence confidence.
6. Recommend a named control owner, action, timeframe and residual-risk target.
7. State the ethical or professional consideration.

## Preferred terminology for the Torridge report

Use precise terms such as **defence in depth**, **least privilege**, **network segmentation**, **secure management plane**, **authentication resilience**, **key lifecycle**, **incident triage**, **evidence correlation**, **rollback**, **third-party assurance** and **data governance** only where supported by evidence.

Avoid unsupported conclusions such as “confirmed breach”, “successful exploitation”, or “unauthorised traffic” unless the Evidence Pack proves them. Prefer “indicator”, “requires validation”, “may permit”, or “evidence does not establish” where appropriate.

## Maintenance rule

Update this matrix only when a new course concept materially changes how an Evidence Pack finding is analysed or how a recommendation is justified. Keep it summarised and do not upload full lecture content to this public repository.
