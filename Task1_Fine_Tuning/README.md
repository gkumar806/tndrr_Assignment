
# Task 1: Fine-tuning with LoRA

## Objective
Fine-tune a small open-weight language model for a banking
customer-intent classification task.

## Model and Dataset
- Base model: Qwen2.5-0.5B-Instruct
- Dataset: Banking77
- Original training examples: 10,003
- Official test examples: 3,080
- Six broad intent categories were created.
- Training/validation split: 9,002 / 1,001

## LoRA Configuration
- Rank (r): 8
- Alpha: 16
- Dropout: 0.05
- Target modules: q_proj, k_proj, v_proj, o_proj,
  gate_proj, up_proj, down_proj
- Learning rate: 2e-4
- Epochs: 3
- Effective batch size: 16
- Optimizer: AdamW
- Weight decay: 0.01
- Precision: FP16

Trainable parameters: 4,399,104
Total parameters: 498,431,872
Trainable percentage: approximately 0.8826%

## Evaluation Results

| Metric | Base Model | Fine-tuned Model |
|---|---:|---:|
| Accuracy | 24.64% | 94.45% |
| Macro F1 | 29.10% | 94.51% |
| Valid JSON | 64.97% | 99.87% |

Evaluation was performed on the held-out validation set of
1,001 examples.

## Failure Analysis
Three failure examples and their analysis are included in
the implementation notebook.

## 7B Model Memory Estimation
Approximate planning estimates:
- Full fine-tuning: 112 GB
- LoRA: 18.5–24 GB
- QLoRA: 6.3–10.2 GB

These estimates depend on precision, optimizer states,
gradients, activations and implementation choices.

## Files
- Task1_Fine_Tuning.ipynb: implementation and experiments.
