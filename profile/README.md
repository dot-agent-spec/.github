# The .agent Protocol Specification (Draft)

## 1. Overview
The **.agent** protocol is an open specification for the encapsulation, distribution, and execution of Artificial Intelligence agents. Unlike isolated scripts or proprietary APIs, the `.agent` format proposes an agnostic exchange standard for hardware and operating systems, enabling intelligence to be portable, secure, and interoperable.

The goal is to allow an agent created for a smartphone to have its logic interpreted or transpiled to run on a smart microwave, a compliance server, or an automotive system.

## 2. Core Conceptual Pillars

### 2.1 Portability: "Build Once, Run Anywhere"
The `.agent` file is a structured package (ZIP) containing metadata, declarations of intent, and execution logic. It does not rely on a specific language runtime (like Python or Node.js) installed on the host, but rather on capabilities provided by the device's **Agent Engine**.

### 2.2 Execution Duality: .flow and .logic
To balance accessibility and performance, the protocol separates execution into two layers:
* **`.flow` (Declarative/Interpreted):** Human-readable files (YAML/JSON) describing state graphs, decision flows, and prompts. This is the ideal layer for "No-Code" creators and for LLMs to understand the agent's strategy before executing it.
* **`.logic` (Pre-compiled/Optimized):** Binaries in intermediate languages (preferably **WebAssembly - WASM**). This layer is intended for heavy logic, mathematical processing, regulatory compliance, or proprietary algorithms requiring native performance and code protection.

### 2.3 Progressive Disclosure
The protocol supports dynamic loading of abilities. An `.agent` file can contain multiple "skills" that are only activated or loaded into memory by the Engine when the flow (`.flow`) or logic (`.logic`) requests them. This allows complex agents to run on resource-constrained devices.

## 3. Model Orchestration and Self-Awareness
To optimize cost, latency, and privacy, the protocol introduces the **Compute Effort** metadata layer. This allows the local Runtime to autonomously decide (or based on user preferences) where each task should be processed.

### 3.1 Effort Scoring
Each skill or task within the `.agent` can declare the required level of reasoning:
* **`effort: low` (Micro-models/Local):** Tasks like short summaries, text classification, or entity extraction. Ideal for on-device models (e.g., Llama-3B, Gemini Nano).
* **`effort: medium` (Mid-tier Models):** Complex drafting, technical reviews, or translation.
* **`effort: high` (Frontier Models/Deep Thinking):** Compliance analysis, complex code generation, or advanced logical reasoning. Requires models like Claude 3.5 Sonnet, GPT-4o, or Gemini 2.0 Pro.

### 3.2 Sub-Agent Decomposition
The protocol allows a main agent (Orchestrator) to instantiate temporary "Worker Agents" from internal skills or external `.agent` files. The Runtime manages communication and context sharing between these sub-agents in an isolated and secure manner.

## 4. The Capability Contract (The Operational Triad)
Interoperability is guaranteed by the explicit declaration of three vectors in the agent manifest:
1.  **Consume (Inputs and Permissions):** What the agent requests from the environment (e.g., `std.contacts`, `std.location`, `fin.bank_statements`).
2.  **Do (Capabilities and Processing):** What the agent can do or requires from the engine (e.g., `ai.vision.ocr`, `math.statistics`, `cooking.timer`).
3.  **Output (Results and Formats):** What the agent delivers at the end of the cycle (e.g., `ui.html_render`, `file.pdf`, `iot.oven.start`).

## 5. Security and Privacy by Design
The model follows the principle of **Declarative Privacy**:
* The device engine acts as a **sandbox**.
* Access to sensitive data is mediated by the OS based on `consume` directives.
* Isolation via **WASI** (WebAssembly System Interface) ensures an agent cannot access host resources (like the file system) that haven't been explicitly mapped.

## 6. Modular and Expandable Ecosystem
Inspired by standards like **JSON-LD** and **Matter**, the protocol uses a namespace-based capability dictionary:
* **`std.*`:** Universal capabilities maintained by the core spec.
* **`com.*` or `custom.*`:** Extensions of the community. This allows industries (e.g., aerospace, medicine) to create their own feature dictionaries.

## 7. Licensing
The protocol and its reference implementations are distributed under the **Apache License 2.0** to ensure adoption by tech giants and independent developers alike.

## 8. Acknowledgments & Authorship
This protocol is proposed and maintained by **[Danilo Borges](https://github.com/daniloborges)**.

The `.agent` protocol stands on the shoulders of existing standards and community efforts. We would like to acknowledge:
* **[Career-Ops](https://github.com/santifer/career-ops):** For the fundamental inspiration regarding operational efficiency and AI agent workflows.
* **[AgentSkills](https://github.com/open-agents/agentskills):** For providing a clear framework for skill-based agent decomposition.
* **[JSON-LD](https://json-ld.org/):** For the semantic structure and linked-data principles that guide our metadata.
* **[Matter (CSA)](https://csa-iot.org/all-solutions/matter/):** For the cluster-based approach to hardware interoperability and universal connectivity.

---

## Current Status: Phase 1 (Draft)
**Current Stage:** Concept Development & Community Feedback.

We are currently:
- [ ] Collecting feedback on the `.agent` conceptual structure.
- [ ] Defining the minimum viable protocol (MVP).
- [ ] Drafting the initial `manifest.json` schema.
- [ ] Building the first reference "Agent Engine" harness.

**Join the Conversation:** We are looking for developers, AI researchers, and hardware manufacturers to help refine this standard. Feel free to open an issue or start a discussion.
