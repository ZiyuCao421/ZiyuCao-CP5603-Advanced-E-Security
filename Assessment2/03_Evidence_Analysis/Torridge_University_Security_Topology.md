# Torridge University — Conceptual Security Topology

> Sanitised architecture view for Assessment 2. It contains no real IP addresses, credentials, configuration values, raw logs, or original evidence files. Connections and control status must be validated against approved private records before operational use.

```mermaid
flowchart TB
  subgraph EXT[External ecosystem]
    U[Students and staff\nInternet and remote access]
    V[Vendors and partners\nSupport and service dependencies]
  end

  subgraph PER[Perimeter and public services]
    FW[Edge controls\nFirewall and filtering]
    DMZ[DMZ\nPublic web boundary]
    PORTAL[Student Portal\nPublic-facing application]
  end

  subgraph CORE[University core and identity]
    NET[Core network\nSegmentation gateway]
    ID[Identity service\nSSO and directory]
    ADMIN[Admin and staff LAN\nManaged endpoints]
  end

  subgraph CLOUD[Cloud and third-party services]
    MFA[MFA provider\nExternal dependency]
    LMS[LMS\nLearning platform]
    GENAI[Enterprise GenAI\nData-governance boundary]
    PLUGIN[LMS plugins\nThird-party integration]
  end

  subgraph BIZ[Critical business systems]
    SIS[SIS application\nStudent records service]
    DATA[SIS data and backup\nConfidentiality and resilience]
    CHG[Change management\nApproval and rollback controls]
  end

  subgraph RES[Research and academic networks]
    RVLAN[Research VLAN\nIsolated network zone]
    LEGACY[Legacy research devices\nCompensating controls]
    JUMP[MFA jump host\nPrivileged administration]
  end

  subgraph SEC[Security operations and governance]
    IDS[IDS and monitoring\nDetection telemetry]
    IR[Incident response\nTriage and escalation]
    IT[Central IT and CAB\nControl ownership]
    GOV[Risk governance\nPolicy and assurance]
    VENDOR[Vendor oversight\nThird-party assurance]
  end

  U --> FW --> DMZ --> PORTAL
  DMZ --> NET --> ID
  ID --> ADMIN
  ID --> MFA
  ID --> LMS
  ADMIN --> GENAI
  LMS --> PLUGIN
  NET --> SIS --> DATA
  DATA --> CHG
  NET --> RVLAN --> LEGACY
  JUMP --> RVLAN

  FW -. telemetry .-> IDS
  DMZ -. telemetry .-> IDS
  DATA -. telemetry .-> IDS
  LEGACY -. telemetry .-> IDS
  IDS --> IR
  IR -. escalation .-> IT
  IT -. control ownership .-> GOV
  GOV -. assurance .-> VENDOR
  GENAI -. governance .-> GOV
  PLUGIN -. oversight .-> VENDOR

  classDef service fill:#E7F0FB,stroke:#43556B,color:#172033;
  classDef exposure fill:#FFE7DF,stroke:#43556B,color:#172033;
  classDef control fill:#E5F5EF,stroke:#43556B,color:#172033;
  classDef governance fill:#F0EAFD,stroke:#43556B,color:#172033;
  class U,V,PORTAL,ID,ADMIN,LMS,SIS,DATA service;
  class DMZ,LEGACY,PLUGIN exposure;
  class FW,NET,IDS,IR,JUMP control;
  class MFA,GENAI,CHG,IT,GOV,VENDOR governance;
```

## Reading guide

- Solid arrows show primary service or access paths.
- Dotted arrows show monitoring, escalation, governance, or assurance relationships.
- Dashed boundaries are logical trust zones, not a verified configuration diagram.
- High-exposure components require specific validation of segmentation, access control, patching, vendor assurance, and compensating controls.


## 简化版拓扑图

```mermaid
flowchart TB
  PEOPLE[人员] --> NET[互联网]
  NET --> CAMPUS[大学网络]
  CAMPUS --> PORTAL[学生门户]
  CAMPUS --> LOGIN[登录]
  LOGIN --> MFA[MFA]
  CAMPUS --> SIS[学生系统]
  CAMPUS --> LMS[学习平台]
  LMS --> PLUGIN[插件]
  CAMPUS --> RESEARCH[研究网络]
  RESEARCH --> DEVICE[研究设备]
  CAMPUS --> GENAI[GenAI]
  CAMPUS --> SECURITY[安全团队]
  SECURITY --> SUPPLIER[供应商]
```


## Simplified Topology (English)

```mermaid
flowchart TB
  PEOPLE[People] --> NET[Internet]
  NET --> CAMPUS[University Network]
  CAMPUS --> PORTAL[Student Portal]
  CAMPUS --> LOGIN[Login]
  LOGIN --> MFA[MFA]
  CAMPUS --> SIS[Student System]
  CAMPUS --> LMS[Learning Platform]
  LMS --> PLUGIN[Plugins]
  CAMPUS --> RESEARCH[Research Network]
  RESEARCH --> DEVICE[Research Devices]
  CAMPUS --> GENAI[GenAI]
  CAMPUS --> SECURITY[Security Team]
  SECURITY --> SUPPLIER[Suppliers]
```
