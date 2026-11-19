# Tndrr AI/ML Assignment

## Project Overview

This repository contains three practical AI/ML tasks focused on Large Language Models (LLMs), Parameter-Efficient Fine-Tuning, Retrieval-Augmented Generation (RAG), and model quantization.

The assignment explores how to improve model performance, build efficient knowledge retrieval systems, and optimize LLM inference with limited GPU resources.

## Tasks Overview

### Task 1: LLM Fine-Tuning Using LoRA

**Objective:** Fine-tune a small language model with 1.5 billion or fewer parameters to improve its task-specific performance.

**Implementation:**
- Applied Low-Rank Adaptation (LoRA) for Parameter-Efficient Fine-Tuning (PEFT).
- Configured the fine-tuning process and training parameters.
- Evaluated model performance using 1,001 evaluation examples.
- Compared the model's performance before and after fine-tuning.
- Analyzed incorrect predictions and documented failure cases.

**Key Result:**
- Initial Accuracy: 24.64%
- Fine-Tuned Accuracy: 94.45%

**Outcome:** Demonstrated how parameter-efficient fine-tuning can significantly improve the performance of a small language model without requiring full model fine-tuning.

### Task 2: Building a RAG Pipeline from Scratch

**Objective:** Develop and evaluate a Retrieval-Augmented Generation (RAG) system using documentation as the knowledge source.

**Implementation:**
- Built a RAG pipeline from scratch using 40 documentation pages.
- Prepared and processed the documentation for retrieval.
- Experimented with two different chunk sizes.
- Implemented and compared multiple retrieval strategies:
  - Semantic Search
  - BM25 Retrieval
  - Hybrid Search
  - Reranking
- Evaluated the pipeline using 15 questions.
- Analyzed retrieval failures and documented the role of BM25 and reranking.

**Outcome:** Explored how chunking strategies and different retrieval techniques influence the relevance and quality of retrieved information in a RAG system.

### Task 3: LLM Quantization and Inference Optimization

**Objective:** Compare different quantization formats to understand their impact on LLM inference speed and GPU memory consumption.

**Implementation:**
- Used Qwen2.5-1.5B through Ollama.
- Performed experiments on an NVIDIA Tesla T4 GPU.
- Compared two quantization formats:
  - Q4_K_M
  - Q8_0
- Evaluated both models using the same 10 prompts.
- Measured inference throughput and additional GPU memory consumption.

**Key Results:**

| Metric | Q4_K_M | Q8_0 |
|---|---:|---:|
| Inference Speed | 138.74 tokens/s | 100.92 tokens/s |
| Additional GPU Memory | 1,182 MB | 1,812 MB |

**Outcome:** Demonstrated the trade-offs between model quantization, inference speed, and GPU memory consumption.

## Key Learning Outcomes

- Understanding Parameter-Efficient Fine-Tuning using LoRA.
- Evaluating LLM performance before and after fine-tuning.
- Building Retrieval-Augmented Generation pipelines from scratch.
- Understanding semantic search, BM25, hybrid retrieval, and reranking.
- Comparing LLM quantization formats.
- Measuring inference throughput and GPU memory usage.
- Performing practical AI/ML experiments and documenting results.

## Repository Structure

The repository is organized into three task-specific sections:

- `Task1/` – LLM fine-tuning using LoRA.
- `Task2_RAG/` – RAG pipeline implementation and evaluation.
- `Task3/` – LLM quantization and inference benchmarking.

Each task contains its respective implementation, experiments, and results.

## Conclusion

This assignment provides hands-on experience across three important areas of modern Generative AI: fine-tuning, retrieval-augmented generation, and inference optimization. It demonstrates practical approaches to improving model accuracy, enhancing knowledge retrieval, and making LLM deployment more resource-efficient.
