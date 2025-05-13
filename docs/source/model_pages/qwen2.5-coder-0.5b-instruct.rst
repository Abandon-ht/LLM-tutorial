`Qwen2.5-Coder-0.5B-Instruct <https://huggingface.co/Qwen/Qwen2.5-Coder-0.5B-Instruct>`_
========================================================================================

Introduction
------------

Qwen2.5-Coder-0.5B-Instruct is Code-Specific Qwen large language models, Significantly improvements in **code generation**, **code reasoning** and **code fixing**.  Key highlights of this model include:

- **Type**: Causal Language Model
- **Training Stage**: Pretraining & Post-training
- **Architecture**: Transformers with RoPE, SwiGLU, RMSNorm, Attention QKV bias, and tied word embeddings
- **Number of Parameters**: 0.49B (0.36B non-embedding)
- **Number of Layers**: 24
- **Number of Attention Heads (GQA)**: 14 for Q and 2 for KV
- **Context Length**: Full 32,768 tokens and generation up to 8,192 tokens

qwen2.5-Coder-0.5B-instruct
---------------------------

- 128 context window

- 1,024 max output tokens

**base model** suitable for the LLM630 Compute Kit, Module LLM, and Module LLM Kit, providing a 128 context window and a maximum output of 1,024 tokens.