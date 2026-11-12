# Part A — Evidence-Based Security Assessment for Torridge University

> **Draft status:** First draft. This document is based on the virtual Evidence Pack and the analysis records in this repository. It should be checked against the official marking rubric, required word count and referencing convention before submission.

## 1. Purpose and approach

This assessment evaluates the security issues indicated by the Torridge University Evidence Pack. The purpose is not to treat every alert as a confirmed incident. Instead, the assessment separates observed facts from inferences, classifies each security issue, explains its likely significance to the university, prioritises treatment, and applies ACS professional ethics to the decisions.

The evidence was first recorded in the Evidence Inventory and Master Evidence Matrix. Each item was then linked to a finding and, where appropriate, to a risk event. This provides a traceable chain from evidence to decision. The assessment uses the following distinctions:

- A **threat** is an actor or event that could cause harm.
- A **vulnerability** is a weakness that can be exploited.
- A **control failure** is a control that is absent, ineffective or too broad.
- A **process issue** is a weakness in governance, approval, review or operational practice.

The risk assessment considers likelihood and impact qualitatively. High-priority findings combine either likely exposure with high-value systems, or control failures that could permit an attacker to move from one service to another. Evidence limitations are retained because the supplied materials may show indicators of compromise without proving that compromise occurred.

## 2. Security context

Torridge University operates a mixed environment containing internet-facing services, student information systems (SIS), learning systems, staff and student access, research areas, laboratory equipment, and third-party services. The topology identifies network boundaries and connections between these areas. This structure makes segmentation, identity resilience, secure device management and data protection particularly important. A weakness at an internet-facing portal or in the network perimeter can create a path towards services that hold student information or support teaching and research.

NIST Cybersecurity Framework 2.0 provides a suitable high-level lens for the case. The framework's Govern, Identify, Protect, Detect, Respond and Recover functions show why technical controls, operational processes and accountable ownership must work together (NIST, 2024). In this case, the technical issues are closely connected to governance issues: several risks arise not only from a vulnerable system but also from incomplete approval, weak review, or unclear ownership.

## 3. Key evidence-based findings

### 3.1 Over-permissive firewall access and the laboratory exception

The firewall configuration includes a broad permit rule and a broad SSH scope (E05). The network overview shows multiple zones that require controlled communication paths (E03). Together, these facts indicate a **control failure** rather than merely a configuration preference. An external attacker or an unauthorised internal user may be able to reach protected services that should be separated by network controls. The potential consequences include lateral movement, service disruption and exposure of university information.

The laboratory exception increases the importance of this finding. The request describes restricted access for legacy laboratory equipment, but its approval state is incomplete (E13). Firewall records include traffic associated with the exception from internal and external addresses (E04). This does not prove malicious or unauthorised activity; it could reflect NAT, vendor maintenance or approved testing. However, the uncertainty itself requires verification because legacy systems are often difficult to patch and an exception can become a persistent route into a more trusted network segment.

This risk is prioritised as high. The immediate action is to review the live rule base and hit counts, remove or narrow any broad permit rule, restrict SSH to authorised administrative sources, confirm the approved source addresses and ports for the laboratory exception, and impose a documented expiry date. The legacy equipment should be isolated and given a replacement or compensating-control plan. NIST SP 800-53 control families support this approach through access control, configuration management and system communications protection (NIST, 2020).

### 3.2 Web portal exposure and hostile activity indicators

The penetration test identified Apache-related weakness and missing HTTP security headers (E01). IDS alerts and web access logs also record scanning and suspicious input patterns directed at the portal (E06 and E07). The application weakness is a **vulnerability**. The scans and suspicious requests are a **threat indicator**. They should not be described as a confirmed compromise because the supplied evidence does not show successful code execution, data access or persistence.

Nevertheless, this is a critical priority because the portal is internet-facing. An attacker may exploit an unpatched platform weakness or an input-handling flaw, leading to disruption, unauthorised access or exposure of connected data. The recommended response is to confirm the portal's version and patch state, remediate the application weakness, implement appropriate security headers, review web application firewall and application logs, and assess file and account integrity. The response must preserve evidence and communicate accurately: urgent investigation is justified, whereas certainty of a breach is not.

### 3.3 Insecure SNMP management

The SNMP query log records use of default community strings or credentials against network devices (E02). The penetration test and IDS alerts provide related evidence of SNMP weakness and activity (E01 and E06). This is a high-priority **vulnerability** because a successful device-management login can expose network configuration, permit unauthorised changes, or help an attacker move through the environment. The current records show queries and alerts, but they do not confirm a successful authentication or configuration change.

Torridge University should change all default secrets, restrict device management to a dedicated administration network, use SNMPv3 where possible, rotate credentials, and review device logs for successful access. These actions align with the access-control and identification-and-authentication focus of NIST SP 800-53 (NIST, 2020). Changes should be scheduled carefully so that essential teaching and research services remain available.

### 3.4 MFA resilience and user behaviour

The MFA incident report describes provider degradation and use of a token cache (E08). During the supplied early incident window, the authentication logs record 58 failures and 12 token-cache successes from 70 events (E09). Staff feedback also reports MFA friction (E15), while the security policy sets expectations for MFA and security management (E10). The principal issue is a **control failure** in identity-service resilience or its operating procedure. The failures may be attributable to the provider incident rather than a hostile attack, so the evidence does not support an account-compromise conclusion.

The risk is still high because identity services control access to many university systems. Users who cannot sign in may turn to unsafe workarounds, while poorly controlled fallback processes can weaken authentication. Torridge University should test MFA failover, define a time-limited and logged fallback process, monitor anomalous activity during outages, and improve user communication and support. Behavioural research is relevant here: security compliance improves when controls are understandable, workable and supported by user awareness (Bulgurcu, Cavusoglu and Benbasat, 2010; Puhakainen and Siponen, 2010). The objective is not to reduce protection for convenience, but to make the secure path usable during normal operation and disruption.

### 3.5 SIS confidentiality, cryptography and change control

The cryptography assessment identifies a strong database encryption algorithm for SIS, but also plaintext backups, TLS 1.0, local key storage and no defined key rotation (E11). The SIS change record lacks a clear rollback plan and shows incomplete Central IT or CAB approval (E12). The first group of issues are **vulnerabilities** in data protection. The second is a **process issue** in change management. Together they create a high-impact risk: student data may be exposed, intercepted or altered, while a failed change may be difficult to recover.

This is a critical risk because SIS contains personal and academic information and supports core university operations. The presence of AES-256 database encryption does not adequately protect plaintext backups or obsolete transport security. The university should encrypt backups, retire TLS 1.0, move keys to a managed and controlled service, establish a rotation process, require approvals for high-impact changes, and document and test rollback procedures. These measures address confidentiality, integrity and availability together. The residual risk should not be considered low until backup restoration and change rollback have been tested.

### 3.6 Third-party LMS plugin and GenAI governance

A faculty email states that a Quiztop LMS OAuth plugin was deployed before Central IT review (E14). This is a **process issue** in third-party application governance. It does not demonstrate a breach or excessive permissions, but OAuth can create a direct path to learning-system or identity information. The university should review scopes, data flows, vendor assurance and contractual controls, then apply least privilege before continuing access.

Staff feedback and teaching-and-learning minutes show uncertainty about data classification and GenAI use, while enterprise accounts and SSO are planned rather than implemented (E15 and E16). This is also a **process issue**. The risks include accidental disclosure of student or staff information, inappropriate use of assessment material, and inconsistent academic practice. The evidence does not prove that sensitive data has been uploaded to a GenAI service. It does establish a governance gap that should be addressed before expanded rollout.

Torridge University should publish an approved-use policy, define prohibited and permitted data types, assess providers, configure enterprise controls, and deliver practical guidance to staff and students. Research on policy compliance supports providing clear, context-appropriate guidance rather than relying on a policy document alone (Siponen, Mahmood and Pahnila, 2014; Albrechtsen, 2007).

## 4. Prioritised treatment plan

The first 14 days should focus on the risks with the most direct combination of exposure and impact: portal remediation and investigation, removal of default SNMP credentials, and immediate review of overly broad firewall rules. The SIS owner should also begin backup-encryption and TLS-remediation planning immediately because the information involved is sensitive and the current backup position is unacceptable.

Within 30 days, the university should validate and reapprove the laboratory exception, test MFA failover, establish a documented fallback process, require SIS rollback plans and approvals, and complete an OAuth scope and vendor review. Within 45 to 90 days, it should implement the GenAI governance model, strengthen management-network segmentation, review firewall rules on a regular schedule, and complete the legacy laboratory equipment plan.

These treatments should be owned by the relevant service manager rather than by a generic security function alone. The risk register assigns owners including the Network Security Manager, Web Services Manager, Identity and Access Manager, SIS Service Owner, Learning Systems Owner and Chief Information Security Officer. This supports accountability and avoids treating cybersecurity as solely a technical matter.

## 5. ACS ethics and professional conduct

ACS professional conduct applies throughout the assessment. Honesty requires clear separation of what the evidence proves from what remains possible but unverified. For example, suspicious portal requests justify investigation but not a public claim that the portal has been breached. Competence requires escalation to specialists where network, cryptographic, identity or incident-response expertise is needed. Respect and protection of the public interest require the university to protect student and staff information, maintain service availability, and communicate material risks and outages honestly.

Ethics also affects prioritisation. A short-term operational inconvenience, such as replacing a default credential or limiting a firewall exception, should be weighed against the privacy and safety of students and staff. At the same time, controls must be proportionate: changing a legacy-lab rule without validating research dependencies could disrupt legitimate work. The appropriate decision is controlled verification, time-limited access, documented approval and compensating protections, not either unrestricted access or unsupported shutdown.

## 6. Conclusion

The Evidence Pack identifies a connected set of technical and governance weaknesses. The highest priorities are internet-facing portal exposure, insecure SNMP management, broad firewall access, and weak protection of SIS data and change processes. MFA resilience, third-party integration and GenAI governance require prompt action because they affect the reliability of access and the protection of university information.

The recommended actions are evidence-based, but several require validation before final conclusions are made. This is particularly important for firewall traffic, IDS alerts and web-log indicators. By addressing the immediate technical weaknesses while improving approval, change, vendor and data-governance processes, Torridge University can reduce both current exposure and the likelihood that similar issues recur.

## References for this draft

- Albrechtsen, E. (2007). A qualitative study of users' view on information security. *Computers & Security, 26*(4), 276–289. https://doi.org/10.1016/j.cose.2006.11.004
- Bulgurcu, B., Cavusoglu, H., & Benbasat, I. (2010). Information security policy compliance: An empirical study of rationality-based beliefs and information security awareness. *MIS Quarterly, 34*(3), 523–548. https://doi.org/10.2307/25750690
- National Institute of Standards and Technology. (2020). *SP 800-53 Rev. 5: Security and Privacy Controls for Information Systems and Organizations*. https://doi.org/10.6028/NIST.SP.800-53r5
- National Institute of Standards and Technology. (2024). *Cybersecurity Framework 2.0*. https://www.nist.gov/cyberframework
- Puhakainen, P., & Siponen, M. (2010). Improving employees' compliance through information systems security training: An action research study. *MIS Quarterly, 34*(4), 757–778. https://doi.org/10.2307/25750704
- Siponen, M., Mahmood, M. A., & Pahnila, S. (2014). Employees' adherence to information security policies: An exploratory field study. *Information & Management, 51*(2), 217–224. https://doi.org/10.1016/j.im.2013.08.006
