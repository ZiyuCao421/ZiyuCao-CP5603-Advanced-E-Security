# Part B — Risk Assessment and Treatment Plan for Torridge University

> **Draft status:** First full narrative draft. This section operationalises the eight evidence-based risks in the risk register. It does not assert a confirmed compromise where the Evidence Pack supplies only a weakness, alert, query, or governance record.

## 1. Assessment approach

Part B converts the Part A findings into a treatment plan. Each risk statement links an asset or process, a plausible threat event, an evidenced weakness or control gap, and a likely consequence. The risk register records likelihood and impact before treatment, the selected treatment, accountable owner, target date, acceptance evidence, review cadence and expected residual rating. This preserves traceability from E01–E16 to decisions without publishing original evidence material.

Inherent risk is assessed before the proposed treatment. Residual risk is the expected position after the stated controls are implemented and independently verified. The ratings are not predictions of a breach. They help Torridge allocate resources according to exposure, asset criticality, possible harm, and the strength and limits of the supplied evidence. This approach applies course principles of defence in depth, least privilege, secure management, incident readiness, recovery and governance. It also reflects the NIST CSF 2.0 view that technical safeguards, governance, response and recovery must operate together (NIST, 2024).

## 2. Treatment priorities

Four risks are assessed as **Critical**. R01 is excessive network access; R03 is portal exploitation; R04 is network-device management compromise; and R06 is SIS confidentiality and integrity failure. These risks have high plausible impact and direct evidence of exposed technical weakness. Their treatment begins in the first 30 days, with R03 and R04 assigned a 14-day response window because of internet exposure, default management access and observed scanning or alert evidence.

R02, R05, R07 and R08 are **High**. R02 concerns an incompletely governed laboratory exception. R05 concerns MFA continuity and the possibility that an outage will cause insecure workarounds. R07 and R08 concern third-party OAuth governance and GenAI data handling. These risks are not lower because they are purely administrative: governance gaps can create access or data-protection failures across several services. They are rated High rather than Critical because the supplied evidence does not prove misuse, excessive permissions, sensitive-data upload or service compromise.

All eight risks use **Reduce** as the primary treatment option. Acceptance would be inappropriate while a reasonable control improvement exists. Avoidance would unnecessarily disrupt teaching, research or institutional services. Risk transfer may be relevant through contracts or insurance, but cannot remove Torridge’s responsibility for access control, data protection or accountable oversight.

## 3. Network, laboratory and management-plane treatments

R01 requires removal or narrowing of the broad firewall permit and restriction of SSH to approved administration sources and roles. The Network Security Manager must validate the live configuration, rule order, NAT context and rule hit counts before changing access. Completion is evidenced by an approved rule review, exported active configuration, segmentation test and SSH allow-list. Alicea and Alsmadi (2021) show that access-control misconfiguration can undermine the protection that a firewall is expected to provide. After successful validation and enforcement, the residual rating is Medium; it remains non-zero because permitted connectivity and configuration change continue to require oversight.

R02 concerns the legacy laboratory exception. The Research IT Manager should document business need, named source, destination, port set, owner and expiry; test the enforced restriction; collect monitored traffic evidence; and isolate the equipment while a replacement plan is developed. This control should be reviewed monthly until the legacy dependency is removed. The current logs do not prove malicious traffic or an unauthorised exception, so the treatment is corrective governance and technical verification rather than an unsupported allegation.

R04 is the most urgent management-plane treatment. Default SNMP credentials or community strings must be removed, SNMPv3 introduced where feasible, management traffic restricted to an administration network, secrets rotated and device logs reviewed. Completion requires configuration evidence and access-control testing, not merely confirmation that passwords were changed. The residual rating is Low because successful SNMP authentication is not evidenced; however, this rating should be reassessed if device-log review reveals a confirmed access event.

## 4. Portal, identity and SIS treatments

For R03, the Web Services Manager must patch the affected platform, remediate the application weakness, apply the missing security headers, assess WAF coverage and preserve/triage relevant alerts. Acceptance requires a patched-version record, header scan, post-fix security test and triage record. IDS and web logs indicate scanning and suspicious input, but they do not prove code execution or data loss. Sommer and Paxson (2010) support treating detection output as contextual investigation input rather than a self-sufficient incident conclusion.

R05 requires a resilient MFA design. The Identity and Access Manager should test provider failover, document a time-bound and logged fallback path, monitor anomalous authentication during disruption, and improve staff communication. Acceptance includes a failover-test result, approved fallback procedure, outage log review and user communication. Ometov et al. (2018) identify that MFA design must consider both security assurance and user acceptance. The objective is therefore an auditable secure path, not lower authentication standards during an outage.

R06 protects SIS data and recoverability. The SIS Service Owner must encrypt backups, retire TLS 1.0 through managed migration, centralise key custody and rotation, require CAB approval for high-impact changes, and test restoration and rollback. Successful treatment evidence includes encrypted-backup proof, transport scan, key-rotation record, approved change record and restore/rollback test. Database encryption alone cannot offset plaintext backup, obsolete transport, weak key lifecycle or an untested recovery process. This remains Medium after treatment because SIS is a high-value system and needs recurring review before material change.

## 5. Third-party and GenAI governance

R07 requires the Learning Systems Owner to inventory OAuth scopes, assess the vendor and data flows, apply least privilege, and obtain Central IT approval before continued use. A scope inventory, vendor assessment and formal approval are the acceptance evidence. The case does not establish excessive permissions or a breach; the treatment addresses the control gap created by deployment before review.

For R08, the Chief Information Security Officer must publish an approved-use policy, define permissible data categories, assess providers, configure enterprise controls and provide practical training. Evidence of completion includes policy publication, an approved-provider register, enterprise configuration and training records. This protects students and staff while allowing appropriate teaching use. Policy communication alone is insufficient: compliance research links awareness, practical fit and organisational culture to secure behaviour (Bulgurcu, Cavusoglu, & Benbasat, 2010; da Veiga, 2016).

## 6. Implementation, assurance and ethics

The roadmap begins with R03 and R04 within 14 days. Within 30 days, Torridge should complete R01, R05, R06 and R07 control work. R08 should be implemented within 45 days, while R02 proceeds to a 60-day replacement or isolation decision. Owners must attach acceptance evidence to the risk register before a status moves from Planned to Complete. Control reviews then follow the stated cadence, and any material change, provider incident or high-impact SIS change triggers reassessment.

ACS ethics applies to the implementation as well as the analysis. Honesty requires reporting residual risk and uncertain evidence accurately. Competence requires appropriately skilled staff to validate network, cryptographic, identity and recovery controls. Respect, public interest and professionalism require protection of student and staff data while avoiding unnecessarily disruptive treatment. A legacy-lab exception, for example, should be time-limited and governed with compensating safeguards rather than accepted indefinitely or shut down without evidence-based planning.

## 7. Conclusion

Torridge’s priority is to reduce demonstrable technical exposure while closing the governance gaps that allow unsafe exceptions, weak recovery practice or unclear data use to persist. The treatment plan assigns clear owners, timeframes and acceptance evidence to all eight risks. Its success depends on verification: an implemented control is not complete until Torridge can demonstrate that it operates as intended and reassess the residual risk.

## References for this draft

- Alicea, M., & Alsmadi, I. (2021). Misconfiguration in firewalls and network access controls: Literature review. *Future Internet, 13*(11), 283. https://doi.org/10.3390/fi13110283
- Bulgurcu, B., Cavusoglu, H., & Benbasat, I. (2010). Information security policy compliance. *MIS Quarterly, 34*(3), 523–548. https://doi.org/10.2307/25750690
- da Veiga, A. (2016). Comparing the information security culture of employees who had read the information security policy and those who had not. *Information & Computer Security, 24*(2), 139–151. https://doi.org/10.1108/ICS-12-2015-0048
- National Institute of Standards and Technology. (2024). *Cybersecurity Framework 2.0*. https://www.nist.gov/cyberframework
- Ometov, A., Bezzateev, S., Mäkitalo, N., Andreev, S., Mikkonen, T., & Koucheryavy, Y. (2018). Multi-factor authentication: A survey. *Cryptography, 2*(1), 1. https://doi.org/10.3390/cryptography2010001
- Sommer, R., & Paxson, V. (2010). Outside the closed world: On using machine learning for network intrusion detection. *IEEE Symposium on Security and Privacy*, 305–316. https://doi.org/10.1109/SP.2010.25
