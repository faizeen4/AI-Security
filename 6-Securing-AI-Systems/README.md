# Securing AI Systems

## Task 01: Introduction
- Learning Objectives
    - Identify the core components of a production AI system and the data flows between them
    - Identify the OWASP LLM Top 10 (2025) and MITRE ATLAS as the primary frameworks for AI threat classification
    - Explain five system-level threat categories: improper output handling, excessive agency, system prompt leakage, unbounded consumption, and sensitive information disclosure
    - Apply secure design patterns, including defence in depth, least privilege, and monitoring to AI system architectures.

## Task 02: Anatomy of an AI System

- When an AI component enters, the picture changes fundamentally: new components appear, and data flows through paths that existing security controls were never designed to monitor.
- PIC SS1
- A trust boundary is where data moves from one security context to another, and every one is a potential attack surface.
- PIC SS2

### Question

What layer in an AI system is responsible for combining the system prompt, user input, and retrieved context before sending it to the model?

### Answer

Prompt Construction

### Question

In the TryAssist architecture, what boundary does LLM output cross when it triggers a database query?

### Answer

LLM-to-tools

## Task 03: The AI Attack Surface

- The OWASP LLM Top 10 (2025) classifies the ten most critical vulnerabilities in LLM applications.
- PIC SS3
- MITRE ATLAS (Adversarial Threat Landscape for AI Systems) is a knowledge base of adversary tactics, techniques, and case studies for AI systems, structured as a counterpart to MITRE ATT&CK. OWASP classifies what the vulnerabilities are. ATLAS documents how adversaries exploit them.
- The NIST AI RMF approaches the problem from an organisational perspective. Its four functions describe how an organisation manages AI risk systematically: Govern (setting policies and accountability structures), Map (identifying AI systems and their risk contexts), Measure (assessing and monitoring risk levels), and Manage (responding to and mitigating identified risks). 

### Question

Which OWASP LLM Top 10 (2025) category covers the risk of LLM output being used to execute SQL injection against a backend database?

### Answer

LLM05

### Question

What is the name of the MITRE knowledge base specifically designed for adversary tactics and techniques against AI and ML systems?

### Answer

ATLAS
