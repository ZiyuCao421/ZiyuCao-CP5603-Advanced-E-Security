# Part C — Executive Brief: Security Priorities and 12-Month Roadmap

> **Draft status:** Working executive brief. Verify all claims, citations, word count and the final required format against the official task sheet before submission.

## Decision for leadership

Torridge University has evidence of material security-control weaknesses but no confirmed compromise. The immediate decision is to fund and govern a phased improvement programme rather than treat each finding as an isolated technical defect. The programme must protect student records and public services, preserve research and teaching access, and require evidence that controls operate as intended.

## Current risk position

The risk register identifies four **Critical** risks: excessive network access (R01), exposed student-portal weaknesses (R03), insecure network-device management (R04), and Student Information System (SIS) confidentiality and integrity failure (R06). Four further risks remain **High**: the legacy research laboratory (R02), MFA resilience (R05), third-party OAuth integration (R07), and GenAI data handling (R08).

The rating reflects the evidence, potential impact on students and University operations, and the uncertainty in existing control effectiveness. For example, alert and scan records require investigation; they do not prove a successful attack. Similarly, policy, approval and planned controls do not demonstrate that a control is operating.

## Decisions requested now

1. **Sponsor a 90-day stabilisation programme.** Give accountable owners authority to remediate portal and device-management exposure, restrict broad network access, and protect SIS recovery data.
2. **Set a risk-acceptance rule.** No Critical exception continues without a named executive sponsor, expiry date, compensating controls and recorded residual-risk decision.
3. **Create a third-party and GenAI governance gate.** Require Central IT review, least-privilege access, approved data handling and re-authorisation for LMS plugins, OAuth and GenAI services.
4. **Require assurance evidence.** Treatment closure requires a configuration record, test result, signed review or restore exercise—not a verbal completion report.

## 12-month roadmap

| Timeframe | Leadership outcome | Priority actions | Evidence of completion |
|---|---|---|---|
| **0–3 months: stabilise** | Immediate exposure reduced | Remove unsafe public exposure; change default device-management settings; recertify firewall rules; encrypt SIS backups; document MFA fallback | Hardened configuration; rule-owner register; encrypted backup; tested fallback record |
| **3–6 months: strengthen** | Core controls are reliable | Retire TLS 1.0; introduce key rotation; restrict privileged access through managed jump paths; complete OAuth/vendor review; test SIS restore and rollback | TLS and key-management records; access review; vendor assessment; restore and rollback test |
| **6–9 months: govern** | Exceptions and suppliers are controlled | Isolate or replace legacy lab components; enforce exception expiry; publish approved GenAI use and data-classification rules; deliver targeted training | Network-isolation test; approved exception register; policy and provider register; training completion |
| **9–12 months: assure and improve** | Improvement is measured and sustained | Independently sample closed treatments; rehearse incident and recovery processes; report residual risk and investment needs to leadership | Assurance report; exercise outcomes; risk trend and next-year plan |

## Measures for leadership review

Monthly for the first quarter and quarterly thereafter, leadership should receive: Critical and High risks open past target; percentage of network rules with a current owner and expiry; portal/device remediation test results; successful SIS restore and rollback results; MFA service and fallback performance; reviewed third-party/OAuth integrations; and completion of GenAI guidance and training. These measures test whether the programme changes risk, not merely whether projects have started.

## Accountability and ethical balance

Technology owners implement controls; service owners accept operational impact; the security function validates evidence; and executive sponsors approve residual risk. Research and teaching requirements do not justify indefinite insecure exceptions: controls must be proportionate, accessible and time-bound. Security communication must distinguish confirmed facts, reasonable inferences and unknowns so decisions are honest, fair and defensible.

## Endorsement sought

Approve the roadmap, executive risk-acceptance rule, accountable owners and assurance reporting cycle. Require an exception escalation whenever a Critical treatment cannot meet its target date.
