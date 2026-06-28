Agentic Exception Navigator (AEN)

Multi‑Agent Case Orchestration for Exception‑Heavy Workflows
Hackathon: UiPath AgentHack 2026  
Core Module: AEN_AssessmentAgent

---

Overview
Agentic Exception Navigator (AEN) is a multi‑agent, human‑in‑the‑loop case orchestration system designed for exception‑heavy enterprise workflows such as loan underwriting, insurance claims, compliance checks, and vendor risk reviews.

AEN uses UiPath Maestro Case, Agent Builder, and API Workflows to coordinate intelligent agents that classify, assess, escalate, and resolve complex cases with full governance and auditability.

The system demonstrates:
- Hybrid intelligence (rules + LLM reasoning)  
- Long‑running case management  
- Human‑in‑the‑loop decisioning  
- Multi‑agent orchestration  
- Enterprise‑grade resilience and audit trails  

---

Architecture
AEN is composed of four core agents orchestrated through Maestro Case:

1. AENIntakeAgent
Parses incoming requests, normalizes data, and creates new cases.

2. AENDocumentAgent
Validates required documents, detects missing items, and triggers reminders.

3. AENAssessmentAgent
Hybrid reasoning engine that produces:
- risk_score  
- risk_level  
- explanation  
- recommended_action  
- exception_flag  

This is the core intelligence layer.

4. AENEscalationAgent
Routes high‑risk or conflicting cases to human reviewers with concise summaries.

---

Maestro Case Lifecycle
AEN uses a structured case lifecycle with deterministic transitions:

1. Intake  
2. Document Collection  
3. Assessment  
4. Human Review  
5. Resolution

Transitions are triggered automatically by agent outputs such as exceptionflag or recommendedaction.

---

Key Features

Hybrid Risk Assessment
AEN_AssessmentAgent combines:
- Deterministic rules  
- LLM reasoning  
- Policy‑based guardrails  
- Exception detection  

Human‑in‑the‑Loop
Cases requiring human judgment are routed to a reviewer UI built with UiPath Apps.

Auditability
Every agent decision, human override, and transition is logged in the case timeline.

Resilience
Retry logic, fallback paths, and exception routing ensure enterprise reliability.

---

AEN_AssessmentAgent (Core Module)

Inputs
- case_id  
- amount  
- income  
- missing_documents  
- required_documents  
- received_documents  
- conflicting_data  
- category  
- raw_payload  
- previousagentnotes  

Outputs
- risk_score  
- risk_level  
- explanation  
- recommended_action  
- exception_flag  
- signals_detected  
- assessment_timestamp  
- assessmentagentversion  

Deterministic Rules
`
IF missingdocuments > 0        → riskscore += 20
IF amount > 50000               → risk_score += 30
IF income < 30000               → risk_score += 25
IF conflictingdata = true      → riskscore += 40
IF category = "highrisk"       → riskscore += 35
`

LLM Reasoning Prompt
Returns JSON with:
- explanation  
- recommended_action  
- exception_flag  

---

Repository Structure
`
agentic-exception-navigator/
│
├── README.md
│
├── /agents
│   ├── AEN_AssessmentAgent/
│   │   ├── schema.json
│   │   ├── logic.md
│   │   ├── deterministic_rules.md
│   │   ├── llm_prompt.txt
│   │   └── sample_inputs/
│   │       ├── case_low.json
│   │       ├── case_medium.json
│   │       └── case_high.json
│   │
│   ├── AEN_DocumentAgent/
│   ├── AEN_IntakeAgent/
│   └── AEN_EscalationAgent/
│
├── /maestro-case
│   ├── case_schema.json
│   ├── transitions.md
│   └── validation_rules.md
│
├── /ui
│   ├── reviewerappmockups.png
│   └── humanreviewflow.md
│
├── /demo
│   ├── demo_script.md
│   ├── screenshots/
│   └── samplecaseflow.md
│
└── /docs
    ├── architecture_diagram.png
    ├── agent_chain.md
    └── roadmap.md
`

---

Demo Flow
1. A new case arrives → IntakeAgent creates case  
2. DocumentAgent checks missing documents  
3. AssessmentAgent calculates risk + explanation  
4. EscalationAgent routes high‑risk cases  
5. Human reviewer approves, rejects, or requests more info  
6. Case resolves with full audit trail  

---

Why This Project Wins
- Real agentic orchestration  
- Enterprise‑grade case management  
- Hybrid intelligence  
- Clear governance and auditability  
- Clean demo flow  
- Modular, extensible architecture  

---

Next Steps
Choose what you want generated next:

- AssessmentAgent schema.json  
- AssessmentAgent logic.md  
- Maestro Case full schema  
- Demo script  

Tell me which one you want and I’ll generate it immediately.
