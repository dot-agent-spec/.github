# The `.agent` Specification 

[Technical Overview](../technical-overview.md)

## 1. Executive Summary

The **.agent** specification is a human-centric standard designed to transform unpredictable AI interactions into reliable, goal-oriented tools. It bridges the gap between human intent and machine execution by focusing on **achieving specific results and fulfilling user objectives.**

By separating **Reasoning (Intelligence)** from **Rules (Governance)**, the specification provides a language-agnostic framework for portable, interoperable, and secure agents. It enables AI to run consistently across diverse environments—from wearables and edge devices to enterprise mainframes.

## 2. Motivation: Solving AI Fragmentation

Current AI implementation mirrors the "Browser Wars" era. Developers face a fragmented landscape where every vendor requires different prompt dialects and governance structures.

### 2.1 Key Challenges

* **Technical Debt:** Engineers must maintain custom logic for every different AI model (OpenAI, Google, Meta, etc.).  
* **Financial Risk:** Without intent declaration, systems may inadvertently route trivial tasks to high-cost frontier models, leading to unnecessary expenses.  
* **Integration Barriers:** Connecting modern AI to legacy systems and diverse hardware ecosystems often requires non-standardized, custom-built bridges, making multi-stage workflows difficult to maintain.

### 2.2 The Solution: Standardized Contracts

The specification introduces a **Standardized Contract**. By declaring required capabilities and effort levels upfront, the system enables **Smart Routing**: choosing the right model (local or cloud) based on task complexity, ensuring efficiency and cost control.

## 3. Core Pillars: The Duality of Execution

To eliminate hallucinations and ensure reliability, the specification separates probabilistic thinking from deterministic rules. This is the relationship between a **Person (The Engine)** and the **Rules (The Governance)**.

### 3.1 The Intelligence Layer (The Reasoning Engine)

Like a human, this layer provides creative synthesis and understanding. It is powerful but requires guidance to remain accurate.

### 3.2 The Governance Layer (The Deterministic Guardrails)

This layer manages the agent's state and lifecycle. It dictates which prompts are dispatched and which system scripts (like cp, sed, or file templates) are executed. It manifests in two ways:

* **Declarative Blueprint (.flow):** A human-readable **Pseudocode** (YAML/JSON). It allows users to build and audit sophisticated agents through transparent instructions.  
* **Optimized Execution (.logic):** A binary layer (Wasm). Designed for enterprise-scale operations requiring high performance, IP protection, or strict regulatory compliance.

## 4. Operational Mechanics

### 4.1 The Capability Contract (Consume, Do, Output)

The specification utilizes the **Jobs To Be Done (JTBD)** methodology to ensure that every agent follows an "Operational Triad" for interoperability:

1. **Consume:** What data does the agent need? (e.g., Calendar access).  
2. **Do:** What actions are required? (e.g., OCR, math, or route calculation).  
3. **Output:** What is the result? (e.g., A rendered HTML UI or a system signal).

### 4.2 Runtime Self-Awareness (Effort Scoring)

The specification uses **Effort Scoring** to allow the local Engine to manage resources autonomously:

* **Low Effort:** Routed to local SLMs (e.g., Gemini Nano) for zero cost and maximum privacy.  
* **Medium Effort:** Balanced between high-end local models and mid-tier cloud services.  
* **High Effort:** Routed to frontier models (e.g., GPT-4o, Gemini Pro) for specialized, complex reasoning.

### 4.3 Universal Portability

The specification acts as a **Universal Adapter**. A single .agent package can be mapped automatically to vendor-specific interfaces like Apple App Intents, Gemini Extensions, or Azure AI Agents without code changes.

## 5. Security & Architecture

* **Zero-Trust Sandboxing:** All logic executes in secure, isolated environments (WASI-compliant).  
* **Permission Mediation:** No access to host resources is granted unless explicitly declared in the "Consume" contract and approved by the user.  
* **Adaptive Loading:** The Engine loads only the necessary components for the current task, maintaining a low memory footprint on edge devices.  
* **Namespace Ecosystem:** Uses std.\* for core primitives and ext.\* for community/industry extensions (e.g., medical or aerospace).

## 6. Practical Applications & Economic Models

### 6.1 Peer-to-Peer (Social)

* **Example:** A shared "Perfect Pizza" agent (`pizza.agent`) sourced from a friend, a culinary influencer, a professional chef, or the pizza brand itself—that configures a smart oven automatically to achieve restaurant-grade results.  
* **Model:** Viral sharing or micro-transactions for lifestyle creators.

### 6.2 Media & Engagement

* **Example:** A Viking-themed brand agent (`viking.agent`). Upon receiving a user's photo, the agent locally generates a personalized Viking warrior avatar. It transforms text messages into a stylized "Norse" dialect and generates stylized audio for social sharing (e.g., converting a simple "Hi, I'm ready" into a booming "SKÀL\! I stand ready for the raid, brother\!").  
* **Model:** Brand loyalty marketing or freemium services.

### 6.3 Cross-System Orchestration (The Interop Journey)

* **Example:** A user issues a voice command on their **Mobile Phone** to prepare for a trip. The agent orchestrates a multi-stage workflow: it triggers the **Smart Vehicle** agent to leave the garage, calls a **Banking Agent** to authorize a parking payment (interfacing with a **Legacy COBOL** system for clearance), and confirms the mission success. By having organized "Do" contracts, these diverse agents collaborate natively without manual integration.  
* **Model:** Enterprise Licensing, infrastructure-as-a-service, or per-transaction orchestration fees.

### 6.4 Scalable Professional Expertise (The 1:N Model)

* **Example:** A traditional (non-IT) law firm creates a single **Modular Contract Validation Agent**. This one-to-many (1:N) asset is deployed across entirely different sectors: it audits loan agreements in **Finance**, audits safety compliance agreements in **Chemical Manufacturing**, and audits procurement agreements in **Aerospace**. The firm scales its core legal expertise as a digital product, allowing disparate industries to "plug in" high-level legal oversight without the firm needing to build custom software for every client.  
* **Model:** High-value B2B service contracts or subscription-based modular expert systems.

## 7. Governance & Roadmap

The .agent specification is a community-driven initiative released under the **Apache License 2.0**.

### Acknowledgments

Proposed by [Danilo Borges](https://github.com/daniloborges), inspired by foundational work from [Career-Ops](https://github.com/santifer/career-ops), [AgentSkills](https://agentskills.io/), [LangGraph](https://langchain-ai.github.io/langgraph/), [AutoGen](https://microsoft.github.io/autogen/), [Model Context Protocol (MCP)](https://modelcontextprotocol.io/), [Matter (CSA)](https://csa-iot.org/all-solutions/matter/), [Wasmtime](https://wasmtime.dev/), [Docker](https://www.docker.com/), and [Kubernetes](https://kubernetes.io/).

### The Path Forward

- [x] **Specification Philosophy & Vision** 
- [ ] **Minimum Specification Structure** 
- [ ] **Community Feedback** 
- [ ] **PoC Release:** Launching a reference Agent Engine.  
- [ ] **Official RFC:** Formal submission for industry review.  
- [ ] **Community Donation:** Transitioning to an open-source foundation for neutral governance.
