# AI Forensics

## Task 01: Introduction

- Learning Objectives
    - Understand the day-to-day challenges faced in DFIR
    - Understand how AI can be used to address those challenges
    - Understand the challenges that arise when you use AI for forensics investigations and the ethical/legal implications this has
    - Understand how AI impacts the DFIR investigation process
      
## Task 02: The AI Forensics Landscape

- PIC FF1

- Accuracy: Accuracy refers to the overall rate of correct predictions. It’s very important when assessing an AI’s performance to not only consider accuracy, as in isolation, it can be very misleading. E
- Precision: Precision measures how often a model's positive predictions are correct.
- Recall: Recall measures how successful the model was in identifying all positives in the provided dataset.
- In conclusion, while AI offers powerful capabilities in DFIR, it's not a silver bullet. Its non-determinism, evaluation challenges, and performance trade-offs mean it should never replace human expertise. AI can accelerate and enhance our work, but human oversight, judgment, and validation will always remain essential. In other words, AI cannot replace humans as digital forensic analysts.

### Question

What ability of AI helps turn a DFIR investigator by recognising patterns they might not have been able to comprehend?

### Answer

Anomaly Detection

### Question

Which metric tells you the proportion of positively flagged results that were actually correct?

### Answer

Precision

### Question

What term describes the AI characteristic where the same input may yield different outputs across different runs?

### Answer

non-determinism

## Task 03: AI & DFIR

- Digital image and video forensics is an excellent example of AI/ML and its capabilities, making our lives in DFIR easier.
- A CNN is a type of neural network that automatically learns patterns in data using small filters commonly used for images.
    - CNN-Based Forgery Detection: Researchers have started combining traditional forensics methods such as ELA (Error Level Analysis, a technique used in image forensics to detect areas of an image that may have been digitally altered) with CNN models to identify image tampering.
    - Deepfake Detection: The advancement of AI technologies has also meant advancements for the attacker. Deepfakes are one area which has seen a dramatic increase in quality, and as a forensics analyst, this is yet another area where new challenges are presented.
    - GANs: Another exciting development in image and video forensics is the use of Generative Adversarial Networks (GANs), a setup where two neural networks compete: one generates fake media, and the other tries to detect it.
- Reconstructing incident timelines is a common and critical part of an investigation; it is also a very labour-intensive and time-consuming task.
    -  Automated Event Timeline Reconstruction: AI systems are particularly adept at correlating time-sequenced data from multiple sources and putting together what happened before, during, and after an incident.
    -  Anomaly Detection: Artificial Intelligence is incredibly good at identifying patterns. It can also be used to determine what constitutes "normal" behaviour for a web application.
- Using some form of AI/ML is now very common in antivirus and endpoint detection response (EDR) products.

### Question

What type of neural network is commonly used in image and video forensics due to its ability to learn spatial patterns in visual data?

### Answer

Convolutional Neural Network

### Question

What kind of analysis can be performed on social media or chat logs to assess the emotional tone of messages?

### Answer

Sentiment Analysis

### Question

What type of data do AI systems correlate to reconstruct the timeline of an incident automatically?

### Answer

Time-Sequenced

### Question

What type of analysis observes how a program behaves to determine whether it is malicious, e.g., using its API call sequence?

### Answer

Dynamic Analysis

## Task 04: AI Legal & Ethical Implications

- 

### Question

What legal test used in the U.S. assesses whether expert or scientific testimony is admissible in court?

### Answer



### Question

What term describes AI models whose internal decision-making processes are difficult to interpret?

### Answer



### Question

What real-world technology used by law enforcement has been shown to produce racially biased results in identifying suspects?

### Answer


### Question

What technique allows machine learning to be performed without transferring sensitive data to a central server, helping preserve privacy?

### Answer


