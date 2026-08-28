# AI Security Threats

## Task 01: Introduction

- Learning Objectives
    - Understand the key vulnerabilities that AI models introduce and how attackers exploit them.
    - Understand how AI is being used to enhance existing attacks like phishing, malware generation, and social engineering.
    - Understand how AI can be used defensively across analysis, prediction, summarisation, and investigation.
    - Understand what it means to adopt AI securely and the frameworks that guide that process.

## Task 02: Vulnerabilities in AI Models

- MITRE have built something similar with a focus specifically on AI threats, called the ATLAS framework. It maps out the tactics, techniques, and procedures attackers use against AI systems.
- https://atlas.mitre.org/matrices/ATLAS
- Prompt Injection occurs when an attacker overrides the original instructions provided to a model.
- Data Poisoning is when an attacker manipulates the training data used to build an AI model, causing its outputs to be incorrect or biased.
- Model Theft occurs when an attacker gains unauthorised access to an AI model, either to steal the intellectual property it represents or to use it for malicious purposes.
- Privacy Leakage refers to the possibility of an AI model inadvertently revealing sensitive information from its training data.
- Model Drift is when a model's performance degrades over time as the world it was trained on changes.

### Question

What MITRE framework was developed specifically to map tactics and techniques used against AI systems?

### Answer

ATLAS

### Question

What AI vulnerability occurs when user input overrides the original instructions provided to a model?

### Answer

Prompt injection

### Question

What attack involves manipulating training data to cause a model to produce incorrect or biased outputs?

### Answer

Data poisoning

### Question

What attack involves repeatedly querying a model's API to train a clone that replicates its behaviour?

### Answer

Model theft

### Question

What term describes the gradual degradation of a model's performance as the environment it was trained on changes over time?

### Answer

Model drift

### Question

What's the flag?

### Answer
PIC AI1
THM{pr0mpt_1nj3ct10n_pwn3d}

## Task 03: AI-Enhanced Attacks

- AI-Generated Malware: Attackers can generate, iterate, and customise malicious code faster than ever, and the models doing the generating have no way to verify the intent behind the request.
- Deepfakes: Given enough training data, an AI can now generate a convincing likeness of a real person, whether that's their voice, their face, or both, to a degree of accuracy that fools even technically aware individuals.
- AI-Enhanced Phishing: Generative AI can produce fluent, contextually appropriate, highly targeted phishing emails at scale and with minimal effort, regardless of the attacker's own writing ability.

### Question

What AI technique is used to generate convincing replicas of a person's voice or appearance?

### Answer

Deepfakes

### Question

What common initial access method has become significantly harder to detect due to AI's ability to generate fluent, targeted content at scale?

### Answer

Phishing

### Question

What's the flag?

### Answer
PIC AI2
THM{s0c_1nb0x_cl34r3d}

## Task 04: Defensive AI

- Analysis: Products like Microsoft Defender for Endpoint and Splunk already leverage AI to analyse input data and surface anomalies at speeds no human analyst could match.
- Prediction: AI models trained on historical attack data can begin to predict future threats before they fully materialise.
- Summarisation:  LLMs can summarise incident reports, extract the key findings from lengthy documents, and draw correlations between events that a human analyst under pressure might miss entirely. That time saving compounds quickly across a busy SOC.
- Investigation: LLMs can be fed raw logs and asked to explain what they show, suggest queries to run, and help triage an active incident in natural language.
  
### Question

According to IBM, how many days faster does AI help identify and contain breaches?

### Answer

108

### Question

What Microsoft product is mentioned as an example of a security tool leveraging AI for analysis?

### Answer

Microsoft Defender for Endpoint

### Question

What defensive AI capability involves feeding an LLM raw logs to help identify what happened during a security incident?

### Answer

Investigation

### Question

What's the flag?

### Answer
PIC AI3
THM{4eg1s_1nc1d3nt_z3r0}

## Task 05: Securing AI

- Securing AI Models: Implementing strong authentication, defining strict access permissions, and using RBAC (Role-Based Access Control) and MFA (Multi-Factor Authentication) significantly reduces the attack surface at the model interaction layer.
- Privacy Protection: Training data should be treated with the same care as any other sensitive data asset: audited, minimised, and encrypted.
- AI Security Standards: Frameworks exist specifically to guide the secure development, deployment, and maintenance of AI systems.
- Model Monitoring:  Explainability tools like SHAP and LIME help make model behaviour more interpretable, giving security teams visibility into what the model is actually doing rather than treating it as a black box.
  
### Question

According to IBM, what percentage of generative AI initiatives are currently secured?

### Answer

24%

### Question

What access control model is recommended to restrict who can interact with AI systems?

### Answer

RBAC

### Question

What ISO standard provides guidance on identifying and mitigating security threats specific to AI systems?

### Answer

ISO/IEC 27090

## Task 06: Practical

### Question

What's the flag?

### Answer

PIC AI4
THM{4l_fund4m3nt4ls_l1c3ns3}
