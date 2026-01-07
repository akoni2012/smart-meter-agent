# Smart Meter Anomaly Detection & Automated Triage (AI Demo)

## Overview
This project is a **demonstration AI solution for the Energy sector**, focused on **smart meter anomaly detection, investigation, and automated triage**.

The demo shows how **AI-driven pattern recognition and orchestration** can be used to:
- Analyse smart meter anomaly incidents
- Determine likely root causes
- Decide whether field engineers are required
- Recommend and automate next actions

The solution combines:
- **IBM watsonx Orchestrate** for agentic workflow orchestration
- **Astra DB Serverless** for scalable incident history retrieval
- **Langflow** for visual AI agent design and prompt orchestration
- **LLMs (OpenAI)** for explainable reasoning over structured energy data

This demo is designed to be **explainable, auditable, and regulator-friendly**, aligning with real-world utility operations.

---

## Problem Statement
Energy suppliers and network operators face challenges including:
- High volumes of smart meter anomalies
- Manual investigation and triage
- Expensive and unnecessary engineer dispatches
- Fragmented data across operational systems

This demo shows how AI can:
- Learn from historical incident patterns
- Provide consistent triage decisions
- Reduce operational costs
- Improve customer experience and grid reliability

---

## Demo Capabilities
- Smart meter anomaly analysis
- Incident pattern recognition (ML-style majority / weighted voting)
- Root cause identification
- Engineer requirement prediction
- Historical resolution lookup ("how was this resolved last time?")
- Explainable decision rationale
- Automated workflow execution

---

## High-Level Architecture
Smart Meter Events
↓
Astra DB Serverless (Incident History)
↓
Langflow (AI Agent & Prompt Logic)
↓
LLM Reasoning (Pattern Recognition)
↓
IBM watsonx Orchestrate
↓
Automated Actions
(Remote reset / Retry / Engineer Dispatch)


---

## Technology Stack

| Component | Purpose |
|--------|--------|
| **IBM watsonx Orchestrate** | Agentic workflow orchestration and action execution |
| **Astra DB Serverless** | Incident history storage and retrieval |
| **Langflow** | Visual AI agent and prompt orchestration |
| **OpenAI LLMs** | Reasoning and explainable inference |
| **JSON / Time-Series Data** | Smart meter telemetry and incidents |

---

## Data Model

### Incident History (Astra DB)
Each incident record includes:
- `incident_id`
- `meter_id`
- `meter_model`
- `firmware_version`
- `location`
- `timestamp`
- `anomaly_type`
- `consumption_kwh`
- `expected_range`
- `root_cause`
- `resolution`
- `engineer_required`

The agent treats the retrieved incident list as a **local training dataset** for pattern recognition.

---

## AI Reasoning Approach

This demo intentionally uses **transparent, explainable ML-style logic** rather than black-box predictions:

- Frequency-based pattern recognition
- Optional recency-weighted voting
- Deterministic decision rules
- Evidence-backed conclusions

Example:
> If 3 out of 4 similar historical incidents did not require an engineer, the agent predicts that an engineer is likely not required — and explains why.

---

## Langflow Agent Design

The Langflow agent:
1. Receives incident history JSON objects from Astra DB
2. Filters incidents based on query context (anomaly type, model, firmware)
3. Applies pattern recognition rules
4. Generates structured, explainable responses
5. Hands off decisions to watsonx Orchestrate

---

## IBM watsonx Orchestrate Integration

watsonx Orchestrate is used to:
- Execute remote remediation actions
- Trigger engineer dispatch workflows
- Route cases to human operators
- Maintain audit trails and approvals

This demonstrates **closed-loop AI automation** in an energy operations context.

---

## Demo Flow (Step-by-Step)

1. Smart meter anomaly detected
2. Incident history retrieved from Astra DB
3. AI agent analyses historical patterns
4. Agent answers triage questions:
   - Is an engineer required?
   - What is the root cause?
   - How was this resolved previously?
5. watsonx Orchestrate executes the recommended action
6. Outcome is logged for future learning

---

## Example Questions the Agent Can Answer
- “Is an engineer required for this anomaly?”
- “What is the most likely root cause?”
- “How was this type of issue resolved last time?”
- “Is the current consumption within expected range?”
- “Summarise recent incidents and recommend next steps”

---

## Explainability & Governance
- All decisions are traceable to specific incidents
- No external knowledge or assumptions are used
- Suitable for regulated energy environments
- Clear separation between reasoning and execution

---

## Getting Started (Demo Setup)

### Prerequisites
- IBM watsonx Orchestrate access
- Astra DB Serverless account
- Langflow installed or hosted
- OpenAI API key

### High-Level Setup
1. Deploy Astra DB schema and load incident history
2. Configure Langflow agent and prompt
3. Connect Langflow to Astra DB and LLM
4. Integrate watsonx Orchestrate actions
5. Run demo scenarios

---

## Extending the Demo
Possible extensions include:
- Gas meter anomalies (dual-fuel)
- EV charger and heat pump data
- Digital twin integration
- Predictive maintenance scoring
- Personalised customer communications
- Regulatory reporting automation

---

## Intended Audience
- Energy utilities and suppliers
- Distribution network operators (DNOs)
- Energy operations and field services teams
- Enterprise architects and AI leaders

---

## Disclaimer
This project is a **demonstration** and does not represent a production-ready system. Data is synthetic and workflows are illustrative.

---

## Contact
For questions or demo walkthroughs, please contact:
Akin


