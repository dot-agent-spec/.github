<!-- 
 Copyright (c) 2026 Danilo Borges (https://github.com/daniloborges)

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

 https://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 -->
 
# The `.agent` Specification: Technical Overview

## 1. Introduction

This document provides a technical deep-dive into the underlying architecture of the `.agent` Specification. It focuses on the conceptual framework for deterministic execution, cross-platform portability, and secure orchestration, acknowledging that specific file formats and low-level standards are currently under refinement.

## 2. Package Anatomy

An .agent package is a portable, self-contained container. The structure decouples user intent from execution logic, allowing for modular updates and audits.

### 2.1 Core Files

Every agent is defined by two files:

* **`agent.description`** — the manifest: identity, capabilities, type declarations, and the Capability Contract (Consume / Do / Output).  
* **`agent.behavior`** — the behavior: state machine, LLM orchestration, and tool calls written in a human-readable DSL.

### 2.2 Supporting Components

* **Knowledge & Persona:** Indexed domain fragments and identity definitions loaded at runtime.  
* **Assets:** Static context templates, prompt fragments, and localized resources.  
* **Security & State:** Digital signatures and encrypted state snapshots for resumable sessions.

### 2.3 Toolchain Packages

| Package | Role |
|---|---|
| `@dot-agent/tree-sitter` | WASM grammar — canonical syntax source |
| `@dot-agent/parser-dsl` | Rust/WASM parser for `.behavior` and `.description` |
| `@dot-agent/kernel-dsl` | Rust/WASM FSM execution engine |
| `@dot-agent/compiler` | Linter, semantic validation, ZIP packaging |
| `@dot-agent/sdk` | Browser-compatible dispatch layer |
| `@dot-agent/language-server` | LSP server for IDE support |

## 3. The Governance Layer: Orchestration & Interop

The Governance Layer acts as the agent's "prefrontal cortex," providing deterministic guardrails.

### 3.1 Representation Formats
The governance of an agent is defined through two complementary formats:
* **`agent.behavior` (Declarative DSL):** A human-readable language with states, handlers, and LLM directives. It empowers non-technical creators to audit and build complex agents via a transparent state machine, allowing the Engine to perform security checks prior to execution.  
* **WASM component (Binary):** Compiled into **WebAssembly**. It handles complex prioritization, high-performance math, or sensitive compliance logic that must remain deterministic and opaque for IP protection.

### 3.2 Transpilation & Framework Mapping

The specification allows for the transpilation of an agent into various target frameworks while keeping the **Intelligence Layer (prompts and knowledge)** intact. This enables a "Write Once, Run Anywhere" model:

* **LangGraph Mapping:** .flow translated to state-graph nodes.  
* **Apple App Intents:** Permissions and capabilities mapped to native iOS/macOS intent schemas.
* **AutoGen/Azure Agents Mapping:** Orchestration logic is mapped to multi-agent conversation patterns and tool-calling definitions.
* **Legacy Bridging:** Logic is transpiled or bridged to interact with specialized systems (e.g., COBOL mainframes or industrial PLCs).


## 4. The Agent Engine Lifecycle

### 4.1 Functional Execution Pipeline
The Engine acts as the supervisor, orchestrating a functional pipeline from the initial user trigger to the final result.
1. **User Input:** Receiving intent via voice, text, or trigger.  
2. **Intent Evaluation:** Analyzing user goals.  
3. **Effort Estimation:** Assessing required resources.  
4. **Capability Routing:** Identifying needed skills.  
5. **Context Policy:** Applying Persona and user personalization.  
6. **Execution Graph:** Navigating the **Governance Layer** (.flow or .logic).  
7. **Model Arbitration:** Selecting the best-fit model (Local SLM vs. Frontier Cloud). 
8. **Reflection:** Self-evaluating output for accuracy and safety.  
9. **Final Synthesis:** Compiling the result.

### 4.2 Cognitive Memory & State Persistence

The specification distinguishes between **carried artifacts** (Persona/Knowledge) and **learned context** managed by the host Engine through custom layered memories.

### 4.3 Permission & Privacy Model (Cross-Device Mediation)

* **Headless Interaction:** If a device lacks a screen (e.g., a smart fridge), the Engine can delegate approval requests to a linked trusted device (e.g., a smartphone notification).
* **Privacy Alerts:** Similar to iOS/Android paradigms, users provide explicit consent for sensitive data access requested in the Manifest.

## 5. Smart Routing & Capability Matrix

| Tier | Complexity | Capability Examples | Recommended Runtime |
| :---- | :---- | :---- | :---- |
| **Tier 1** | Simple/Utility | Context compression, chat summarization, local scripts. | Local SLM (on-device) |
| **Tier 2** | Specialized | Local/Cloud Vision, high-speed parsing. | Local High-end or Mid-tier Cloud |
| **Tier 3** | Deep Thinking | Multi-step planning, high-stakes logic. | Frontier Cloud (Pro Models) |

## 6. Development & Distribution

* **Authoring:** Writing `agent.description` and `agent.behavior` files directly, with IDE support via `@dot-agent/language-server` (LSP), or using AI-assisted generators.  
* **Compiling:** `@dot-agent/compiler` lints, validates semantics, and packages the agent into a distributable ZIP. The WASM component targets the specification's binary format for high-performance logic.  
* **Distribution:** Direct sharing via Instant Messaging (as `.agent` files) or vendor marketplaces.
