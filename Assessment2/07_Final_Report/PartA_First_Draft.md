# Part A — Evidence-Based Security Assessment for Torridge University

> **Draft status:** Incremental revision 2. This version applies the course knowledge matrix and a separately audited comparison draft. It uses the full 16-item virtual Evidence Pack. Findings distinguish what the evidence shows from what requires validation.

## 1. Purpose and method

This assessment identifies and prioritises security issues in the Torridge University Evidence Pack. Each conclusion follows an evidence chain: observed fact, classification, realistic threat event, potential impact, priority and treatment. A **threat** is an actor or event that may cause harm; a **vulnerability** is an exploitable weakness; a **control failure** is a missing, ineffective or over-broad control; and a **process issue** is a weakness in governance, approval or operational practice.

The course framework requires defence in depth rather than reliance on a single appliance or policy. It also requires incident preparation, response and recovery. Therefore, alerts are treated as triggers for correlation and triage, not as proof that exploitation succeeded. This approach also accords with ACS expectations of honest professional communication: a report must not imply certainty that the evidence does not provide.

## 2. Security context and evidence reconciliation

Torridge combines internet-facing services, SIS, learning systems, research networks, legacy laboratory equipment and third-party services. The topology makes segmentation, secure device management, resilient authentication and data protection central safeguards. NIST CSF 2.0 is a useful organising lens: governance, technical controls, detection, response and recovery must operate together (NIST, 2024).

A key cross-evidence issue is control visibility. E05 records a broad permit rule and broad SSH scope, while E04 contains firewall events including exception-related traffic and other policy outcomes. E13 describes a narrower business exception for legacy laboratory equipment. These records cannot yet be reconciled into one verified enforcement picture: they may reflect different devices, rule order, NAT, changed configuration or incomplete extracts. The security finding is therefore not that every observed connection was unauthorised. It is that Torridge lacks sufficient current evidence to demonstrate that approved policy, active configuration and observed traffic are consistently reconciled. Firewall research supports traffic-informed review of decaying, unused or inconsistent rules rather than treating a static rule export as complete assurance (Golnabi et al., 2006; Alicea & Alsmadi, 2021).

## 3. Evidence-based findings

### 3.1 Network access and the laboratory exception

E05 contains an overly broad permit rule and broad SSH scope. E03 shows distinct network zones that should communicate through controlled paths. This is a **control failure**: over-permissive filtering and inadequate segmentation may give an external attacker or unauthorised internal user a route to protected services. The likely impacts are lateral movement, disruption and exposure of university information.

E13 increases the significance of the finding because it documents a legacy-lab firewall exception with incomplete approval status. E04 records traffic associated with this exception from more than one source context. The evidence does not establish that the traffic was malicious or unapproved; vendor maintenance, NAT and incomplete logging context remain plausible alternatives. However, the exception cannot be treated as effectively governed until Torridge verifies the active source allow-list, ports, rule order, expiry, approvals and device isolation. The immediate treatment is to remove or narrow broad rules, limit SSH to authorised administrative sources, time-limit the exception and review live hit counts. These actions implement course concepts of least privilege, segmentation and defence in depth.

### 3.2 Portal exposure, SNMP and detection evidence

The penetration-test report identifies Apache-related weakness and missing HTTP security headers (E01). Web and IDS records show scanning and suspicious input patterns against the portal (E06 and E07). The platform or configuration weakness is a **vulnerability**; the scanning and suspicious requests are **threat indicators**. They do not establish successful execution, data access or persistence. The correct response is prompt incident triage: confirm version and patch state, preserve relevant logs, inspect application and account integrity, and assess whether compensating controls are operating.

E02 also records queries using default SNMP community strings or credentials, with related penetration-test and IDS evidence (E01 and E06). This is a high-priority **vulnerability** because successful device-management access could disclose configuration, enable unauthorised changes or facilitate movement through the network. The evidence records queries and alerts, not confirmed authentication or configuration change. Torridge should change default secrets, restrict management traffic to a dedicated administration network, use SNMPv3 where feasible, rotate secrets and inspect device logs.

The IDS evidence demonstrates detection activity but does not include a disposition, containment record or forensic outcome. Detection must therefore be correlated with firewall, web, endpoint and authentication records. Sommer and Paxson (2010) show why intrusion-detection output needs operational interpretation rather than black-box acceptance. This supports an investigation requirement, not a claim that Torridge failed to respond or was compromised.

### 3.3 MFA resilience and user experience

The MFA incident report records provider degradation and token-cache use (E08). Authentication logs show 58 failures and 12 token-cache successes in the supplied early window (E09). Staff feedback identifies MFA friction (E15), and policy E10 sets an expected security baseline. This is a **control failure** in identity-service resilience or its operating procedure. The evidence does not prove account takeover, and token-cache success alone does not prove an intentionally fail-open design. It does justify assurance testing of the fallback path.

Identity controls protect access to many university systems, so the risk remains high. Torridge should test failover, define a time-bound and logged fallback process, monitor anomalous activity during outages and improve user communication. MFA research identifies both authentication strength and user acceptance as design concerns (Ometov et al., 2018). The objective is not to weaken MFA for convenience, but to provide a usable, auditable secure path during normal operation and provider disruption.

### 3.4 SIS data protection and change control

E11 identifies AES-256 database encryption for SIS alongside plaintext backups, TLS 1.0, local key storage and no defined key rotation. E12 shows a SIS change record without a clear rollback plan and with incomplete Central IT or CAB approval. The first group are **vulnerabilities** in confidentiality and cryptographic lifecycle management; the latter is a **process issue** in change management. Together they could expose, intercept or alter student information and make service recovery difficult.

This is critical because SIS holds personal and academic information and supports core operations. Database encryption does not compensate for plaintext backups, obsolete transport protection or weak key custody. The required treatment is to encrypt backups, retire TLS 1.0 through managed migration, centralise and rotate keys, require approval for high-impact changes, and document and test restoration and rollback. This follows the course focus on protection at rest and in transit, key lifecycle, recovery and accountable change control.

### 3.5 Third-party, GenAI and human governance

E14 states that a Quiztop LMS OAuth plugin was deployed before Central IT review. This is a **process issue** in third-party governance. It is not evidence of a breach or excessive permission. It does support a least-privilege review of OAuth scopes, data flows, vendor assurance and approval before continued access.

E15 and E16 show uncertainty about data classification and GenAI use while enterprise accounts and SSO remain planned rather than implemented. This is also a **process issue**. The records do not prove that sensitive data has been uploaded to GenAI. They do show that guidance and controls should precede broader adoption. Torridge should publish an approved-use policy, define permissible data types, assess providers, configure enterprise safeguards and give staff and students practical guidance. Policy reading and security culture are linked, but a policy document alone does not establish safe practice (da Veiga, 2016; Siponen, Mahmood, & Pahnila, 2014).

## 4. Prioritisation and treatment

The first 14 days should address portal triage and patching, removal of default SNMP access, review of broad firewall rules and commencement of SIS backup and TLS remediation. Within 30 days, the university should validate and reapprove the laboratory exception, test MFA fallback, require SIS rollback and approval evidence, and complete OAuth and vendor review. Within 45–90 days, it should implement GenAI governance, strengthen management-network segmentation, establish periodic firewall recertification and complete the legacy-equipment plan.

Priorities reflect the combination of exposure, asset value, plausible impact and evidence confidence. The portal, SNMP, firewall and SIS items are highest because they concern externally reachable or high-value systems and have direct technical evidence. MFA, third-party and GenAI issues are high governance priorities because weak access resilience or unclear data practice can undermine several systems at once.

## 5. ACS ethics and professional conduct

ACS ethics is integrated into each decision. Honesty requires reporting portal and IDS evidence as indicators rather than asserting a breach. Competence requires qualified network, cryptography, identity and incident-response specialists to validate findings and implement controls. Respect and public interest require protection of student and staff information while maintaining teaching and research continuity.

Ethical treatment must also be proportionate. Restricting a legacy laboratory exception or replacing a default credential may create operational friction, but leaving access unnecessarily broad transfers risk to students, staff and the university. The appropriate course is documented approval, time-limited access, compensating safeguards and transparent communication—not unrestricted access or an unsupported shutdown.

## 6. Conclusion

The Evidence Pack indicates connected technical and governance weaknesses. The immediate priorities are portal exposure, insecure SNMP, excessive network access and weak SIS protection and change control. MFA resilience, third-party access and GenAI governance require prompt treatment because they affect the reliability of access and protection of university information.

The main systemic issue is not proof of a single confirmed intrusion. It is the gap between documented intent, active controls and evidence of operation. Torridge should close that gap through evidence reconciliation, least privilege, control testing, incident readiness and accountable governance.

## References for this draft

- Albrechtsen, E. (2007). A qualitative study of users' view on information security. *Computers & Security, 26*(4), 276–289. https://doi.org/10.1016/j.cose.2006.11.004
- Alicea, M., & Alsmadi, I. (2021). Misconfiguration in firewalls and network access controls: Literature review. *Future Internet, 13*(11), 283. https://doi.org/10.3390/fi13110283
- Bulgurcu, B., Cavusoglu, H., & Benbasat, I. (2010). Information security policy compliance. *MIS Quarterly, 34*(3), 523–548. https://doi.org/10.2307/25750690
- da Veiga, A. (2016). Comparing the information security culture of employees who had read the information security policy and those who had not. *Information & Computer Security, 24*(2), 139–151. https://doi.org/10.1108/ICS-12-2015-0048
- Golnabi, K., Min, R. K., Khan, L., & Al-Shaer, E. (2006). Analysis of firewall policy rules using data mining techniques. *IEEE/IFIP NOMS*, 305–315. https://doi.org/10.1109/noms.2006.1687561
- National Institute of Standards and Technology. (2020). *SP 800-53 Rev. 5*. https://doi.org/10.6028/NIST.SP.800-53r5
- National Institute of Standards and Technology. (2024). *Cybersecurity Framework 2.0*. https://www.nist.gov/cyberframework
- Ometov, A., Bezzateev, S., Mäkitalo, N., Andreev, S., Mikkonen, T., & Koucheryavy, Y. (2018). Multi-factor authentication: A survey. *Cryptography, 2*(1), 1. https://doi.org/10.3390/cryptography2010001
- Puhakainen, P., & Siponen, M. (2010). Improving employees' compliance through information systems security training. *MIS Quarterly, 34*(4), 757–778. https://doi.org/10.2307/25750704
- Siponen, M., Mahmood, M. A., & Pahnila, S. (2014). Employees' adherence to information security policies. *Information & Management, 51*(2), 217–224. https://doi.org/10.1016/j.im.2013.08.006
- Sommer, R., & Paxson, V. (2010). Outside the closed world: On using machine learning for network intrusion detection. *IEEE Symposium on Security and Privacy*, 305–316. https://doi.org/10.1109/SP.2010.25
