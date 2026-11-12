# External Draft Audit — Part A Improvement Record

## Scope

This audit reviews a comparison draft produced in a separate tool. It is treated as untrusted analytical input, not as evidence. The review tested its reasoning against the full 16-item virtual Evidence Pack, the course knowledge matrix, and independently checked publication metadata for sources adopted below.

## Useful elements adopted

| Contribution | Audit result | Adoption in this repository |
| --- | --- | --- |
| Cross-evidence reconciliation | Strong method. Comparing rules, logs, requests and approvals reveals control-visibility gaps. | Added to the Part A draft as a reconciliation and validation section. |
| Firewall policy lifecycle focus | Directly relevant to E04, E05 and E13. | Added Alicea and Alsmadi (2021) and Golnabi et al. (2006). |
| Alert interpretation caution | Useful when framed as a limitation of detection evidence. | Added Sommer and Paxson (2010) only to support the need for operational interpretation, not to assert that an incident occurred. |
| MFA usability and resilience emphasis | Relevant to the provider degradation and staff feedback evidence. | Added Ometov et al. (2018) to support the broader security-usability trade-off. |
| Policy-culture link | Relevant to MFA and GenAI governance. | Added da Veiga (2016) to the literature matrix. |

## Findings not adopted as facts

- The external draft analysed only a subset of the Evidence Pack. It cannot replace the 16-item evidence inventory in this repository.
- An alert-only IDS record does not prove that no response occurred. The case evidence supports a finding that response or disposition evidence was not supplied.
- Token-cache successes during an MFA-provider incident do not, by themselves, prove a fail-open design or an account compromise. The report therefore calls for failover and assurance testing.
- Firewall traffic from additional source addresses does not alone prove an unauthorised exception or malicious activity. NAT, vendor activity, and incomplete configuration context remain alternative explanations.
- A paper about open-source software supply-chain attacks is not direct evidence of OAuth scope overreach in a hosted LMS plugin. The report retains a least-privilege and vendor-assurance recommendation without using that paper as direct support.
- Australian regulatory material mentioned in the external draft is not automatically applicable to a university. It is excluded from Part A unless the assignment brief or case establishes that legal scope.

## Independently verified additions

- Alicea, M., & Alsmadi, I. (2021). *Misconfiguration in Firewalls and Network Access Controls: Literature Review*. Future Internet, 13(11), 283. https://doi.org/10.3390/fi13110283
- Golnabi, K., Min, R. K., Khan, L., & Al-Shaer, E. (2006). *Analysis of Firewall Policy Rules Using Data Mining Techniques*. IEEE/IFIP NOMS, 305–315. https://doi.org/10.1109/noms.2006.1687561
- Sommer, R., & Paxson, V. (2010). *Outside the Closed World: On Using Machine Learning for Network Intrusion Detection*. IEEE Symposium on Security and Privacy, 305–316. https://doi.org/10.1109/SP.2010.25
- Ometov, A., Bezzateev, S., Mäkitalo, N., Andreev, S., Mikkonen, T., & Koucheryavy, Y. (2018). *Multi-Factor Authentication: A Survey*. Cryptography, 2(1), 1. https://doi.org/10.3390/cryptography2010001
- da Veiga, A. (2016). *Comparing the Information Security Culture of Employees Who Had Read the Information Security Policy and Those Who Had Not*. Information & Computer Security, 24(2), 139–151. https://doi.org/10.1108/ICS-12-2015-0048

## Result

The revised Part A uses the comparison draft's strongest contribution—evidence reconciliation—while retaining course-aligned terms, the full evidence scope, and explicit limits on what the supplied evidence proves.
