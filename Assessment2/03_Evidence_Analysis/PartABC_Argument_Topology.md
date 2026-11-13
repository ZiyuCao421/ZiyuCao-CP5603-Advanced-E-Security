# Part A–C Argument Topology

> Public-safe conceptual map. It uses evidence IDs and assessment conclusions only; it contains no original evidence, raw logs, credentials, personal data or sensitive configuration values.

~~~mermaid
flowchart LR
  subgraph INPUT[Evidence basis]
    E1[E01–E07
Network and public-service evidence]
    E2[E08–E10
Identity and policy evidence]
    E3[E11–E12
SIS protection and change evidence]
    E4[E13–E16
Governance, third-party and GenAI evidence]
  end

  subgraph A[Part A — Evidence assessment]
    A1[Observed facts
and evidence limitations]
    A2[Security findings
classified by type]
    A3[Significance for services,
data and operations]
  end

  subgraph B[Part B — Risk and treatment]
    B1[R01–R08
prioritised risk register]
    B2[Controls, owners, targets
and residual risk]
    B3[ACS ethics, privacy,
accessibility and trade-offs]
  end

  subgraph C[Part C — Leadership action]
    C1[Decisions requested
fund, govern, accept risk]
    C2[12-month roadmap
stabilise → strengthen → govern → assure]
    C3[Assurance measures
and escalation]
  end

  subgraph OUT[Desired outcomes]
    O1[Protected student data
and SIS recovery]
    O2[Safer public services
and network access]
    O3[Secure, practical teaching
and research]
  end

  E1 --> A1
  E2 --> A1
  E3 --> A1
  E4 --> A1
  A1 --> A2 --> A3
  A3 --> B1 --> B2 --> B3
  B1 --> C1
  B2 --> C2
  B3 --> C1
  C1 --> C2 --> C3
  C3 --> O1
  C3 --> O2
  C3 --> O3

  classDef evidence fill:#E7F0FB,stroke:#43556B,color:#172033;
  classDef assessment fill:#FFF3D6,stroke:#43556B,color:#172033;
  classDef risk fill:#FFE7DF,stroke:#43556B,color:#172033;
  classDef action fill:#E5F5EF,stroke:#43556B,color:#172033;
  classDef outcome fill:#F0EAFE,stroke:#43556B,color:#172033;
  class E1,E2,E3,E4 evidence;
  class A1,A2,A3 assessment;
  class B1,B2,B3 risk;
  class C1,C2,C3 action;
  class O1,O2,O3 outcome;
~~~

## How to read the map

- **Part A** turns the Evidence Pack into bounded findings: a policy, alert or approval is not treated as proof of an operating control or successful attack.
- **Part B** turns those findings into prioritised risk statements, practical treatments, accountable owners and explicit residual-risk decisions.
- **Part C** turns the treatment plan into leadership decisions, a 12-month programme and measures that show whether controls actually operate.

This is a traceability map, not an operational network diagram. Use the [Torridge University security topology](Torridge_University_Security_Topology.md) for the conceptual technical architecture.
