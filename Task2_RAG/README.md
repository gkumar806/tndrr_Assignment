
# Task 2: Retrieval-Augmented Generation from Scratch

## Objective
Build a document retrieval and question-answering pipeline
without LangChain or LlamaIndex.

## Document Collection
- Source: Official Scikit-learn User Guide
- Pages collected: 40
- Approximate words: 122,834
- Embedding model: sentence-transformers/all-MiniLM-L6-v2
- Embedding dimension: 384

## Chunking
Two chunking configurations were evaluated:

- Small chunks: 200 words, 40-word overlap, 782 chunks.
- Large chunks: 500 words, 80-word overlap, 305 chunks.

## Retrieval Evaluation
15 manually written questions were used.
The evaluation metric measures whether the expected source
page appears in the top-k retrieved results.

### Semantic Retrieval

| Metric | 200-word chunks | 500-word chunks |
|---|---:|---:|
| Recall@1 | 0.9333 | 1.0000 |
| Recall@3 | 1.0000 | 1.0000 |
| Recall@5 | 1.0000 | 1.0000 |
| MRR | 0.9667 | 1.0000 |

### BM25 Retrieval

| Metric | 200-word chunks | 500-word chunks |
|---|---:|---:|
| Recall@1 | 0.8667 | 0.8000 |
| Recall@3 | 0.8667 | 0.8000 |
| Recall@5 | 1.0000 | 0.9333 |
| MRR | 0.8967 | 0.8267 |

### Hybrid Retrieval (RRF)

| Metric | 200-word chunks | 500-word chunks |
|---|---:|---:|
| Recall@1 | 1.0000 | 0.9333 |
| Recall@3 | 1.0000 | 1.0000 |
| Recall@5 | 1.0000 | 1.0000 |
| MRR | 1.0000 | 0.9556 |

### Hybrid + Cross-Encoder Reranking
Cross-encoder: cross-encoder/ms-marco-MiniLM-L-6-v2

For 200-word chunks, Recall@1, Recall@3, Recall@5 and
MRR were all 1.0000.

All 15 expected source pages were ranked first.

Note: These are source-page retrieval metrics, not exact
passage accuracy or answer-generation accuracy.

## BM25 and Reranking
BM25 adds keyword-based retrieval, helping find documents
containing important exact terms. A reranker takes retrieved
candidates and scores them again using a more detailed
query-document relevance model.

## Failure Analysis
Three retrieval failure cases and possible improvements
are documented in the notebook.

## Files
- Task2_RAG.ipynb: complete implementation and experiments.
- Additional data and metric files can be added to this folder.
