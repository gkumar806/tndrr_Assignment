
# Task 3: Local LLM Inference and Quantization

## Objective
Run and compare two quantized versions of the same open model
using Ollama.

## Environment
- Model: Qwen2.5-1.5B-Instruct
- Inference engine: Ollama
- GPU: NVIDIA Tesla T4 (15 GB)
- Test prompts: 10
- Temperature: 0
- Context length: 2048 tokens
- Maximum generated tokens: 120

## Benchmark Results

| Metric | Q4_K_M | Q8_0 |
|---|---:|---:|
| Model size | 986 MB | 1.6 GB |
| Generated tokens | 1180 | 1153 |
| Generation time | 8.51 sec | 11.43 sec |
| Tokens per second | 138.74 | 100.92 |
| Additional GPU memory | 1182 MB | 1812 MB |

Memory figures are approximate additional total GPU memory,
calculated by subtracting the baseline measurement. They are
not isolated model-only measurements.

## Output Quality
Both models were tested on the same 10 prompts and manually
reviewed for correctness, clarity, relevance and completeness.

Both produced broadly comparable responses. Q8 sometimes
provided more detail, but no consistent quality advantage
was observed in this manual comparison.

## KV Cache
KV cache stores previously calculated Key and Value vectors
during autoregressive generation. It avoids recalculating
attention information for earlier tokens.

Its memory requirement increases with context length and
the number of concurrent requests.

## Quantization
Quantization reduces the number of bits used to represent
model weights. Four-bit weights require approximately one
quarter of the raw storage of FP16 weights, before metadata
and runtime overhead.

## Serving 20 Concurrent Users
Proposed architecture:

Users -> API Gateway -> Request Queue -> Inference Server -> GPU

Assumptions:
- 1.5B Q4 model.
- 20 concurrent users.
- Approximately 4096 context tokens per user.

Estimated memory:
- Model weights: 1.2 GB
- KV cache: 2.3 GB
- Runtime and GPU workspace: 3-5 GB
- Total: approximately 6.5-8.5 GB

This is a planning estimate, not a measured 20-user load test.
Continuous batching, request queuing and rate limiting are
recommended for serving.

## Conclusion
Q4_K_M was approximately 37.5% faster and used approximately
34.8% less additional GPU memory than Q8_0 in this experiment.

## Files
- Task3_Local_Inference.ipynb: implementation and experiments.
