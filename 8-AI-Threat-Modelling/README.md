# AI Threat Modelling

## Task 01: Introduction

- Traditional threat modelling provides a strong foundation, and frameworks like STRIDE have helped defenders systematically identify security threats for over two decades.
-  But AI systems introduce assets, behaviours, and failure modes that those frameworks weren't designed to handle. Training data can be poisoned. Model weights can be stolen. Prompts can be injected. And the outputs? They're non-deterministic, meaning the same system can behave differently each time it's queried.
- Learning Objectives
     - Identify AI-specific assets and attack surfaces that don't exist in traditional applications
     - Apply STRIDE threat categories to AI/ML system components with appropriate context
     - Use MITRE ATLAS to enumerate adversarial techniques targeting AI systems
     - Map OWASP LLM Top 10 risks to architectural components to identify where threats live and how to prioritise them
     - Produce a structured threat assessment for an AI deployment

## Task 02: AI-Specific Assets and Attack Surfaces

- AI systems change the picture. They introduce an entirely new class of assets that most security teams have never had to inventory, classify, or defend. Missing these assets during a threat assessment means missing entire categories of risk, and that's exactly the gap attackers exploit.
- PIC HM1
- AI systems aren't just traditional applications with a model bolted on. They have different assets, behaviours, and ways of failing, and our threat models need to account for all of it.

### Question

In a RAG-based system, which AI asset type is used to retrieve relevant context at query time?

### Answer

Embedding Vectors

### Question

An attacker gains access to MegaCorp's model registry and swaps the production model for a modified version. Which AI-specific asset has been compromised? 

### Answer

Model Registry / Artifacts
