# LLM Security

## Task 01: Introduction

-Learning Objectives
    - Understand LLM-specific vulnerabilities that do not apply to traditional ML systems.
    - Recognise how LLMs create new attack surfaces through natural language interfaces and memory/context mechanisms.
    - Identify and categorise LLM threat types: data-based, model-based, system-based, user-based.
    - Understand the realistic risks LLMs introduce in production systems.
- The LLM landscape can be broken down into four categories: data-based threats, model-based threats, system-based and user-based threats.

## Task 02: Data-Based Threats

-  LLMs are fundamentally data-driven; they learn from a corpus of training data and generate outputs based on it.
-  Sometimes LLMs can inadvertently leak data by design because they memorise and regurgitate patterns from their training data.
-  Training Data Extraction
    - Training data extraction attacks generate large amounts of text from an LLM and analyse those outputs to identify sequences that show behavioural signs of memorisation, such as unusually high likelihood/confidence, deterministic regeneration (a model's ability to reproduce the same output), or realistic structured content (this information is especially easy to access if the attacker has white box access).
- Membership Inference
    -  Unlike extraction, this attack doesn't involve generating candidate outputs; rather, it focuses on confirming whether a sample the attacker already has was in the training set.
    -  A model typically performs better (e.g. predicts with higher confidence or lower loss) on examples it has seen during training than on new, unseen examples. Attackers leverage this by querying the model with the target example and measuring indicators such as confidence scores, likelihoods, or perplexities.
- Prompt Leakage (LLM07:2025 — System Prompt Leakage)
    - LLMs like ChatGPT, Claude, Gemini, etc., don't just operate using the learnings from their training data; they also use hidden instructions known as system or developer prompts.
    - If the user's input cleverly convinces the model to regurgitate or summarise the entire conversation , the model may comply. This attack is a type of prompt injection (covered in more detail later in the room) and is possible because, to the LLM, the system prompt and the user's messages are all just parts of the conversation history.

### Question

Which sample is a member?

### Answer

PIC LLM1
MI_SAMPLE_ALPHA

### Question

Which attack determines whether a known data sample was part of an LLM’s training set?

### Answer

Membership inference

### Question

Which data-based threat involves the model reproducing memorised snippets of its training data?

### Answer

Training data extraction

## Task 03: Model-Based Threats

- Model-based threats exploit the model itself as the attack surface, abusing how information is encoded within its parameters and representations.
- Model Extraction
    - Model extraction is the process of illicitly copying a machine learning model's functionality or parameters without authorisation.
    - An attacker can do this if they can interact with an LLM through its public API and send a large number of prompts; the responses to these prompts are then stored in a sort of input-output pair.
- Model Inversion
    - Model inversion attacks exploit a model's output to reveal information about its training data.
    - Instead of testing whether a known example was seen during training, the attacker iteratively queries the model to reconstruct unknown training data that has been encoded into its parameters or representations.  

### Question

What is the employee ID?

### Answer

PIC LLM2
7814

### Question

Which model-based threat attempts to reconstruct sensitive information encoded within a model’s internal representations?

### Answer

Model inversion

## Task 04: System-Based Threats

- Unlike traditional software, LLMs process all input (system instructions, user prompts, etc.) as a single concatenated context without a built-in security boundary separating trusted content (i.e., the system instructions) from untrusted content (i.e., user prompts).
- Prompt Injection
    - At a system level, it is enabled by what can be described as context-window poisoning: the manipulation of the model's input context to override or subvert its intended behaviour.
    - From the model's perspective, all tokens inside the context window are treated uniformly during inference. Attackers can leverage this lack of distinction to sometimes convince the LLM to ignore its system instructions and do something nefarious instead, essentially inverting the untrusted/trusted relationship.
- Context Overflow (LLM10:2025 — Unbounded Consumption)
    - Context window overflow attack happens when an attacker supplies an extremely long input or continuously appends content until the context is overfull. The LLM's context works like a FIFO (First In, First Out) buffer: once it's full, adding new tokens causes the earliest tokens to be dropped.
    - Mitigation: Implement rate limiting, token budgets, and cost alerting. In pay-per-use deployments, unbounded consumption is a financial attack surface; flooding an API with oversized prompts can run up significant costs intentionally, a pattern known as Denial of Wallet (DoW).
- Memory Poisoning
   - Many LLM deployments (such as chatbots) maintain stateful conversations, meaning the model's input at each turn includes a history of previous dialogue (or the model at least retains some memory of past interactions).
   -  This persistent conversation state opens the door to memory poisoning attacks, where an attacker gradually injects malicious or misleading information into the dialogue history, influencing later outputs. Unlike one-shot prompt injection, these attacks play out over multiple turns/inputs.

### Question

Did you convince the model? Whats the flag?

### Answer

PIC LLM3
THM{MEMORY_POISONED}

### Question

Which system component combines system instructions, retrieved data, and user input into a single sequence?

### Answer

The Context Window

## Task 05: User-Based Threats

- LLM Powered Social Engineering
    -  An LLM can now generate spear-phishing emails that read exactly like a colleague or executive.
- Trust Exploitation (LLM09:2025 — Misinformation)
    -  Users might accept an AI's answer without double-checking, even if it's completely fabricated (a hallucination) or manipulated by an attacker. Threat actors actively exploit this trust. In fact, one security threat is human manipulation via LLMs, with attackers leveraging users' faith in AI to influence decisions.
    - Package hallucination is an occurrence that can happen, for example, when developers are using an LLM as a coding assistant and the LLM hallucinates fake software package names or updates.

### Question

Which package should you NOT download?

### Answer

PIC LLM4
robbco-llm-audit

### Question

LLM-powered social engineering primarily amplifies which existing attack category?

### Answer

Phishing





