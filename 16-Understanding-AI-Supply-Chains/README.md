# Understanding AI Supply Chains

## Task 01: Introduction

- Learning Objectives
    - Explain what an AI supply chain is and how it differs from a traditional software supply chain
    - Identify the four key components of an AI supply chain (models, datasets, frameworks, dependencies)
    - Map the attack surface across model, dependency, data, and infrastructure layers
    - Recognise real-world supply chain incidents and the trust relationships they exploited

## Task 02: What Is a Supply Chain?

- Supply chain attacks are effective because they exploit trust rather than bypass defences. Instead of attacking your application directly, an attacker compromises something your application already trusts.
- The key insight here is that supply chain attacks scale efficiently. When an attacker successfully compromises one widely used component, they gain access to every system that depends on it.

### Question

In the SolarWinds attack, where in the supply chain was the malicious code injected?

### Answer

Build Process

### Question

While installing torch Pip also pulls in filelock, which you never listed. What type of dependency is filelock?

### Answer

Transitive Dependency

## Task 03: The AI Supply Chain

- Traditional software supply chains deal primarily with code (including libraries, frameworks, and packages written by developers). AI supply chains add a fundamentally different type of artefact: trained models.
- A trained model is not just code. It is the product of an architecture (the neural network structure), training data (potentially millions of examples), a training process (the settings and hardware configuration), and serialised weights (the learned parameters saved to a file).
- <img width="1200" height="660" alt="image" src="https://github.com/user-attachments/assets/a51671c0-f2e9-459d-a2fd-2e8bc154c62b" />
- <img width="1800" height="720" alt="image" src="https://github.com/user-attachments/assets/b054e753-4965-4a10-a177-abe18c4c257b" />
- <img width="1200" height="600" alt="image" src="https://github.com/user-attachments/assets/f033bc6d-0459-41dd-99fc-9be4ff3261d7" />

### Question

What are the four key components of an AI supply chain? (listed alphabetically)

### Answer

datasets, dependencies, frameworks, models

### Question

What do model files contain that allows them to run code when loaded?

### Answer

Serialised Objects

## Task 04: Two Ways to Consume AI

-  There are two fundamentally different ways organisations consume AI models, and each creates a different risk profile.
-  Paradigm 1: Downloading Model Files
    - This is the traditional approach, where you download pre-trained weights (.pkl, .safetensors, .pt, .gguf, etc.) from a repository like Hugging Face and load them into your own infrastructure. You are responsible for hosting, inference, and security.
    - GGUF models are almost always quantised. Quantisation compresses a model's weights from full precision (32-bit floating-point) to lower precision (4- or 8-bit integers), reducing file size so large models can run on consumer hardware. If a third party performed that compression, the quantisation step is itself an unverified point in the supply chain.
- Paradigm 2: Calling Models via API
    - Organisations consume AI through hosted API services from providers such as OpenAI, Anthropic, and Google, or aggregators such as OpenRouter.
    - When you call a model through an API, you are trusting the provider's entire pipeline: their training data curation, fine-tuning decisions, hosting security, and update practices. You cannot verify any of these independently. The supply chain is still there; it is simply hidden behind an API call.

### Question

What is the dominant file format for running local large language models such as LLaMA, Mistral, and Qwen?

### Answer

gguf

## Task 05: The Four Attack Layers

- Layer 1: The Model Layer
    - Serialisation-level: Code hidden inside the file format itself, and executes when the file is loaded
    - Architecture-level: Malicious logic embedded in the model's layers, executed on every prediction
    - Weights-level: Learned values subtly altered to misbehave on specific inputs
    - Stripping executable code from a model file eliminates serialisation-level attacks but leaves architecture-level and weights-level attacks completely untouched. Effective defence requires inspection at every level. 
- Layer 2: The Dependency Layer
    - This layer covers the packages and libraries your ML project depends on. Attackers exploit it through dependency confusion, typosquatting, and uploading malicious packages with professional-looking descriptions that hide malware.
- Layer 3: The Data Layer
    - Training data is the foundation of every ML model, and poisoning it is difficult to detect. Researchers have demonstrated that replacing as little as 0.1% of a training dataset with crafted samples can introduce a reliable backdoor without measurably affecting accuracy on clean data.
- Layer 4: The Infrastructure Layer
    - The infrastructure layer covers the systems that host, distribute, and manage AI artefacts. Attackers gain access to model or package repositories, inject malicious steps into CI/CD build pipelines, or steal maintainer credentials to push malicious updates under trusted identities.

### Question

At which layer of the AI supply chain do pickle-based attacks occur?

### Answer

Model Layer

### Question

Which level of model attack is eliminated by converting to SafeTensors format?

### Answer

Serialisation-level

### Question

Researchers find that 0.1% of a public training dataset has been replaced with crafted samples designed to introduce a backdoor. Which attack layer does this represent?

### Answer

Data Layer

## Task 06: Real-World Incidents

- Incident 1: PyTorch Dependency Confusion (December 2022) https://pytorch.org/blog/compromised-nightly-dependency/
- Incident 2: Hugging Face Hub Vulnerabilities (2023–2024)
- Incident 3: Ultralytics Build Pipeline Compromise (December 2024)
- Incident 4: @solana/web3.js Compromise (December 2024)
- Incident 5: NullifAI Scanner Evasion on Hugging Face (February 2025)
  
### Question

The torchtriton package exploited pip's version resolution to install a public package over an internal one. Which of the four attack layers does this target?

### Answer

Dependency Layer

### Question

The @solana/web3.js attacker stole a maintainer's credentials to push malicious updates to a legitimate, high-trust repository. Which attack layer does this represent?

### Answer

Infrastructure Layer

## Task 07: Practical

- Solved using TryHackME's provided model page
  
### Question

In the static site, what is the name of the unverified organisation that uploaded the model?

### Answer

trustworthy-ai-models

### Question

How many downloads does this model have (last month)?

### Answer

127

### Question

What file format does the verified model (google-bert/bert-base-uncased) use for its weights?

### Answer

SafeTensors
