`Qwen2.5-0.5B-Instruct <https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct>`_
============================================================================

Introduction
------------

Qwen2.5-0.5B-Instruct is part of the Qwen2.5 series, featuring instruction-tuned language models with 0.5 billion parameters. Key highlights of this model include:

- **Type**: Causal Language Model
- **Training Stage**: Pretraining & Post-training
- **Architecture**: Transformers with RoPE, SwiGLU, RMSNorm, Attention QKV bias, and tied word embeddings
- **Number of Parameters**: 0.49B (0.36B non-embedding)
- **Number of Layers**: 24
- **Number of Attention Heads (GQA)**: 14 for Q and 2 for KV
- **Context Length**: Full 32,768 tokens and generation up to 8,192 tokens

This model demonstrates significant improvements in instruction following, generating long texts, and understanding structured data. It supports multilingual capabilities across 29 languages, including English, Chinese, French, and more.

qwen2.5-0.5B-ax630c
-------------------

- 128 context window

- 1,024 max output tokens

- ttft 359.8ms

- avg-token/s 10.32

**base model** suitable for the LLM630 Compute Kit, Module LLM, and Module LLM Kit, providing a 128 context window and a maximum output of 1,024 tokens.

qwen2.5-0.5B-p256-ax630c
------------------------

- 256 context window

- 1,024 max output tokens

- ttft 1126.19ms

- avg-token/s 10.30

**Long-Context Model** Compared to the base model, it provides extended context capabilities, offering a 256 context window and a maximum of 1,024 output tokens.

qwen2.5-0.5B-Int4-ax630c
------------------------

- 128 context window

- 1,024 max output tokens

- ttft 442.95ms

- avg-token/s 12.52

**The INT4 quantized model** compared to the base model, provides faster inference speed, providing a 128 context window and a maximum output of 1,024 tokens.