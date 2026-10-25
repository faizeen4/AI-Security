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

## Task 03: Data Supply Chain and STRIDE's Gaps

- PIC HM2
- STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege), has been the backbone of threat modeling since Microsoft introduced it in the late 1990s. It remains highly effective for traditional applications. But when applied to AI systems without adaptation, it has documented gaps:
- PIC HM3

### Question

An attacker injects crafted data points into a training pipeline over several months, gradually shifting the model's decision boundaries. At which supply chain stage does the attacker inject the malicious data?

### Answer

Data Collection

### Question

Which STRIDE category is insufficient for capturing the delayed, diffuse effects of training data poisoning?

### Answer

Tampering

## Task 04: Adapting Stride for AI Systems

- S — Spoofing
    - Traditional: Impersonating a legitimate user or service.
    - In AI: Injecting fake data into trusted sources to mislead the model.
    - Examples: Fake RAG documents, fake AI APIs, fooling facial or voice recognition.
- T — Tampering
    - Traditional: Illegally modifying data or files.
    - In AI: Poisoning training data to make the model learn incorrect patterns.
    - Examples: Model weight manipulation, prompt injection, altering input features.
- R — Repudiation
    - Traditional: Denying an action due to missing logs.
    - In AI: Inability to trace or explain why a model made a decision.
    - Examples: Missing audit logs, unrecorded prompts/context, unclear model versions.
- I — Information Disclosure
    - Traditional: Exposing sensitive information.
    - In AI: Stealing model functionality or extracting confidential data.
    - Examples: Model extraction, training data leakage, system prompt leakage, embedding inversion.
- D — Denial of Service
    - Traditional: Overloading a system to make it unavailable.
    - In AI: Exhausting AI computing resources or increasing API costs.
    - Examples: Expensive queries, GPU exhaustion, sponge examples, disrupting training.
- E — Elevation of Privilege
    - Traditional: Gaining unauthorised higher-level access.
    - In AI: Bypassing safety guardrails to access restricted capabilities.
    - Examples: Jailbreaking, excessive tool permissions, tool misuse, cross-plugin escalation.
- What STRIDE Still Misses
    - Adversarial examples: Inputs that fool AI predictions; may fit multiple STRIDE categories.
    - Model bias: Unfair decisions not covered by traditional STRIDE threats.
    - Emergent behaviours: Unexpected AI capabilities or behaviours that traditional threat models may not predict.

### Question

What is the primary AI-specific manifestation of Information Disclosure in the STRIDE-AI mapping?

### Answer

Model Extraction

### Question

An attacker crafts prompts that cause an LLM to bypass its safety guidelines and content restrictions. Which STRIDE category does this map to?

### Answer

Elevation of Privilege

### Question

Which OWASP LLM Top 10 (2025) entry addresses the risks of AI systems being granted too many permissions or too much autonomy? 

### Answer

LLM06: 2025 — Excessive Agency

### Question

An attacker drives your monthly inference bill from $15,000 to $180,000 without taking your service offline. What is this type of attack commonly called?

### Answer

Denial of Wallet

## Task 05: MITRE ATLAS: The AI Threat Technique Catalogue

- ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems) is a knowledge base of adversary tactics and techniques targeting AI and ML systems.
- 5 Key MITRE ATLAS Techniques
    - Data Poisoning (T0020): Injecting malicious training data. → Tampering
    - Model Extraction (T0024): Stealing a model by querying its API. → Information Disclosure
    - Evade ML Model (T0015): Fooling a model into misclassification. → Tampering, Spoofing, or Elevation of Privilege
    - LLM Prompt Injection (T0051): Injecting malicious instructions directly or through retrieved content. → Tampering
    - Backdoor ML Model (T0018): Hiding triggers in a model to cause malicious behaviour. → Tampering
- STRIDE + ATLAS
1. STRIDE: Identify what could go wrong.
2. ATLAS: Understand how attackers execute the attack.
3. Mitigations: Apply countermeasures to prevent or reduce attacks.
Key takeaway: STRIDE identifies threats; ATLAS provides attack techniques and defenses.

### Question

What does the acronym ATLAS stand for?

### Answer

Adversarial Threat Landscape for Artificial-Intelligence Systems

### Question

Which ATLAS case study described a self-replicating prompt injection worm that spread between AI agents via RAG email systems?

### Answer

Morris II 

### Question

What is the ATLAS technique ID for Model Extraction?

### Answer

AML.T0024

## Task 06: OWASP LLM Top 10:Mapping Risks to Components

- The OWASP Top 10 for LLM Applications is a community-driven list of the most critical security risks specific to large language model deployments. Published by the OWASP GenAI Security Project, it's built from real-world incidents, researcher findings, and industry consensus.
- OWASP LLM Top 10 
    - LLM01 — Prompt Injection: Malicious inputs manipulate model behaviour.
    - LLM02 — Sensitive Information Disclosure: AI reveals confidential data.
    - LLM03 — Supply Chain: Compromised models, datasets, or dependencies.
    - LLM04 — Data and Model Poisoning: Corrupted data or weights alter model behaviour.
    - LLM05 — Improper Output Handling: Unvalidated AI outputs cause downstream vulnerabilities.
    - LLM06 — Excessive Agency: AI has excessive permissions or tool access.
    - LLM07 — System Prompt Leakage: Internal instructions or secrets are exposed.
    - LLM08 — Vector and Embedding Weaknesses: Vulnerabilities in RAG, embeddings, or vector databases.
    - LLM09 — Misinformation: AI generates convincing but false information.
    - LLM10 — Unbounded Consumption: Excessive resource usage causes high costs or DoS.

### Question

How many of the OWASP LLM Top 10 entries affect the LLM Inference Endpoint?

### Answer

7

### Question

An organisation notices their chatbot is rendering LLM output directly in the browser without sanitisation. Which OWASP entry does this fall under?

### Answer

Improper Output Handling

### Question

Which component in a typical LLM architecture is the primary one that needs hardening against data and model supply chain risks (LLM03)?

### Answer

Training Pipeline
