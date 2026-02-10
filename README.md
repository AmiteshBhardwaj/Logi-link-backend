# 📦 Logi-Link: Serverless RAG Architecture

**Logi-Link** is a low-latency, declarative AI agent designed to unify **Structured Logistics Data** (SQL/Table) with **Unstructured Policy Documents** (Vector Embeddings).

## 🏗️ Architecture Overview

This project utilizes a **Declarative Serverless Stack**. Instead of maintaining monolithic server code, the application logic is defined through strict schema constraints and system-level prompt engineering.

### 📂 Repository Structure

* `src/agent_logic.md`: **Core Logic.** Contains the "System 2" reasoning rules, privacy guardrails (PII redaction), and strict Markdown rendering instructions.
* `database/schema.json`: **Data Layer.** Defines the strict typing for shipment IDs (`SHP-XXXXXX`) and Enums for status tracking (preventing invalid states like "Null" locations).
* `public/index.html`: **Client Side.** A lightweight, asynchronous frontend wrapper designed to load instantly on low-bandwidth networks (3G/4G).

## 🔧 Technical Implementation

### 1. The Data Layer (Zapier Tables)
We enforced a schema-first approach to ensure data integrity.
* **Type Safety:** `Status` columns are locked to specific Enums (`In Transit`, `Delivered`).
* **Regex Validation:** Shipment IDs must match `^SHP-\d{6}$`.
* *(See `database/schema.json` for full definition)*

### 2. The Reasoning Engine (RAG)
The agent uses a Hybrid Retrieval method:
* **Vector Search:** For "fuzzy" questions like *"What is the insurance policy?"*
* **Deterministic Lookup:** For precise questions like *"Where is SHP-001542?"*

## 🚀 Deployment
The frontend is deployed via a CDN-backed interface to ensure <100ms Time-To-First-Byte (TTFB).

---
*Built for the IDT 2025-26 Sem-I CSE14 class by Amitesh Bhardwaj,Karitkeya Verma,Sarthak Kashyap and Abhishek Kumar*
