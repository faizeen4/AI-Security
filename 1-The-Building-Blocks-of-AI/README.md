# The Building Blocks of AI

## Task 01: Introduction

- Learning Objectives
    - Understand what AI and ML are and how they relate to each other.
    - Understand how Machine Learning algorithms work and the categories they fall into.
    - Understand Deep Learning and neural networks, and why they matter.
    - Understand what LLMs are and how they work under the hood.

## Task 02: Introducing TryHackMe's AI Agent Platform

- Rather than a traditional terminal or virtual machine, some tasks in this room use an AI agent as your interactive environment. I
- This isn't just a chatbot. Each agent in this room has been configured with a specific role, a set of behaviours, and in some cases, information it's protecting or a goal it's trying to achieve.

## Task 03: What is AI and Machine Learning?

- Artificial Intelligence refers to a machine or computer system that is able to carry out tasks that would otherwise require human reasoning, comprehension, problem-solving, or creativity.
- ML is a subfield of AI that refers to a computer's ability to learn from data without being explicitly given instructions.
- Models require ongoing monitoring and periodic retraining as the world changes around them, which is what makes it an iterative process rather than a one-and-done job.

### Question

What is the term for when a model becomes too familiar with its training data and fails to generalise to new data?

### Answer

Overfitting

### Question

What is the subfield of AI that enables systems to learn from data without being explicitly programmed?

### Answer

Machine Learning

## Task 04: Machine Learning Algorithms

- ML algorithms are the mathematical methods used to learn patterns from data.
- The trained outputs they produce are what we call ML models.
- Every algorithm follows the same basic structure: a decision process that makes predictions based on input data, an error function that evaluates how far off those predictions were, and a model optimisation process that adjusts the algorithm to do better next time. This loop repeats until the model reaches a satisfactory level of performance.
- ML algorithms fall into four main categories depending on how they learn and what kind of data they work with: Supervised, Unsupervised, Semi-supervised and Reinforcement learning .

### Question

Which category of ML algorithm learns by receiving rewards or penalties based on actions taken in an environment?

### Answer

Reinforcement learning

### Question

Which category of ML algorithm uses a small amount of labelled data to guide learning across a larger unlabelled dataset?

### Answer

Semi-supervised learning

### Question

What's the flag?

### Answer

PIC AI1
THM{4lg0r1thm_4g3nt}

## Task 05: Neural Networks and Deep Learning

- A neural network is made up of layers of nodes, where each node represents a neuron and each connection between nodes acts as a synapse. The input layer receives raw data. The number of nodes it has depends on the data type: a 4x4 pixel image, for example, has 16 input nodes, one per pixel. The hidden layers in the middle process and refine that input, extracting increasingly complex features as the signal moves deeper. Each connection carries a weight that determines how much influence it has on the next layer. The output layer produces the final prediction.
PIC AI3
- When a network has more than three layers, it qualifies as a Deep Learning (DL) algorithm, hence the name.

### Question

What is the first layer in a neural network that receives raw input data?

### Answer

Input layer

### Question

What term describes the weighted connections between nodes in a neural network?

### Answer

Synapses

### Question

What's the flag?

### Answer

PIC AI2
THM{n3ur0n_1_0nl1n3}

## Task 06: Large Language Models

- Large Language Models are deep learning-based AI models that process and generate text by predicting the next word in a sequence.
- LLMs are first trained in a pre-training phase, where they process enormous volumes of text.
- The scale of pre-training is only possible because of advances in hardware (specifically GPUs enabling parallel processing) and a specific type of neural network called transformer neural networks.
- After pre-training, humans come back into the loop in a process called RLHF (Reinforcement Learning from Human Feedback).
- Artificial Intelligence is the overarching field. Machine Learning is a subfield of AI that enables learning from data. Deep Learning is a subfield of ML that uses neural networks to process data at scale without human intervention. Large Language Models are advanced DL models built on transformer neural networks, designed to understand and generate human-like text.

### Question

What type of neural network, introduced by Google in 2017, powers modern LLMs?

### Answer

Transformer neural networks

### Question

What is the name of the process where humans review and flag model outputs to refine its behaviour after pre-training?

### Answer

RLHF

### Question

What mechanism do transformer networks use to assign different levels of importance to different words in a sequence?

### Answer

Attention

### Question

What algorithm is used to adjust a model's parameters based on the difference between its prediction and the correct answer?

### Answer

Backpropagation

## Task 07: Practical

### Question

What algorithm is used to adjust a model's parameters based on the difference between its prediction and the correct answer?

### Answer

PIC AI4
THM{y0u_tr41n3d_th3_n3tw0rk}



