# AI System Reconnaissance

## Task 01: Introduction

- AI reconnaissance is the practice of identifying components, understanding what they are, and what they expose. You still use tools like Nmap and curl, but the targets are different. Standard scanning wordlists and service detection miss AI infrastructure entirely because they were not built to find it.

## Task 02: The AI Infrastructure Stack

- Model Serving

    - Loads trained models and exposes prediction APIs.
    - NVIDIA Triton: Ports 8000 (HTTP), 8001 (gRPC), 8002 (metrics).
    - TensorFlow Serving: Ports 8500 (gRPC), 8501 (HTTP).
    - TorchServe: Ports 8080 (inference), 8081 (management), 8082 (metrics).
    - Ollama: Port 11434.
    - vLLM: Commonly port 8000.
    - Security relevance: Exposed APIs may allow unauthorised inference, model enumeration, resource abuse, or access to management functions.
    - Recon endpoints: /v2/models, /api/tags, /v1/models

- ML Orchestration & Experiment Tracking

    - Manages training pipelines, experiments, and distributed computing jobs.
    - MLflow: Port 5000; stores experiment parameters, metrics, and model artifacts.
    - Kubeflow: Commonly uses ports 80/443; manages ML pipelines and deployments.
    - Ray: Dashboard commonly uses port 8265; other services may use port 8000.
    - Security relevance: Misconfigured interfaces may expose research data, credentials, training jobs, or unauthorised job-execution capabilities.
    - Remember: The ShadowRay campaign targeted exposed Ray infrastructure.

- Vector Databases

    - Store numerical representations of documents (embeddings) for semantic search and Retrieval-Augmented Generation (RAG).
    - Qdrant: Ports 6333 (HTTP), 6334 (gRPC).
    - Weaviate: Port 8080.
    - Milvus: Port 19530.
    - Chroma: Commonly port 8000.
    - Security relevance: Unauthorised access may expose stored documents, sensitive metadata, or internal knowledge sources.
    - Recon endpoints: /collections, /v1/schema

- Model Registries

    - Store model files, versions, deployment stages, and artifact locations.
    - Common formats include .pkl, .pt, .onnx, and .mar.
    - Security relevance: Unauthorised access may expose proprietary models, intellectual property, and deployment details. Unsafe deserialisation of untrusted model files can also create code-execution risks.

- Supporting Infrastructure

    - Jupyter Notebook (8888): Interactive coding environment. Weak authentication may expose notebooks and code execution; notebooks may contain hardcoded credentials.
    - MinIO (9000/9001): S3-compatible object storage. Weak access controls may expose datasets, model artifacts, and checkpoints.
    - Prometheus metrics: Commonly exposed through endpoints such as /metrics. May reveal model names, GPU utilisation, request rates, and infrastructure details.
    - Security relevance: These services can expose sensitive data, enable unauthorised execution, or reveal internal infrastructure.

- Important Ports to Remember

    - 5000: MLflow
    - 8000: Triton, vLLM, and other services
    - 8265: Ray Dashboard
    - 8888: Jupyter
    - 9000/9001: MinIO
    - 11434: Ollama
    - 6333: Qdrant

### Question

What is the IP address of the host running an HTTP service on port 8888 in your scan results?

### Answer

<img width="855" height="897" alt="image" src="https://github.com/user-attachments/assets/0376eac0-5f0b-492f-9d9e-e706faa16168" />

10.10.45.20

### Question

Which port does MLflow Tracking Server run on by default?

### Answer

<img width="857" height="886" alt="image" src="https://github.com/user-attachments/assets/b985f4a1-7e4d-4329-8175-2f8c83b27647" />

5000


