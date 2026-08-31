# Prompt Engineering

## Task 01: Introduction

- Learning Objectives
    - Understand what tokens are and how LLMs process text
    - Grasp nondeterminism and why LLMs produce variable outputs
    - Control model behaviour using temperature, max tokens, and top-p
    - Understand the four pillars of effective prompt engineering
    - Recognise the difference between system and user prompts
    - Understand key prompting techniques

## Task 02: LLM Fundamentals

- LLM models breaks text into tokens and the model converts each token into a unique number (an ID). The model only works with these numbers, using them to predict what number (token) should come next. 
- Different models use different tokenisation methods: GPT uses Byte-Pair Encoding, while BERT uses WordPiece. The same sentence produces different token sequences depending on which model you're using.
- Temperature: The Randomness Dial
    - Temperature is the most important parameter .
    - This is a numerical value, commonly ranging from 0.0 - 2.0 (which can differ between providers) that controls how "adventurous" the model is when picking its next word.
- Max Tokens: The Length Limiter
    - Max tokens caps how long the response can be.
    - Consumer models, like those on paid plans like OpenAI, charge per token, so controlling length is a cost-control measure.
- Top-P: The Alternative Randomness Dial
    - Top-p (nucleus sampling) is temperature's cousin.
    - The higher the value, the bigger the shortlist; the lower the value, the more restricted the model's choices.
    - In general, it is advised to adjust temperature OR top-p, but not both. Using both simultaneously creates unpredictable interactions because you're stacking two randomness controls.
- Context Window: The Memory Limit
    - Every model has a context window: its maximum "working memory" measured in tokens.

### Question

What is the term for the smallest units that an LLM breaks text into in order to process it?

### Answer

Tokens

### Question

What parameter would you set to 0.0 to make an LLM behave as close to deterministic as possible?

### Answer

Temperature

### Question

What parameter restricts which tokens the model considers by limiting selection to a cumulative probability mass?

### Answer

Top-p

### Question

What term describes the maximum working memory of an LLM, measured in tokens?

### Answer

Context window
