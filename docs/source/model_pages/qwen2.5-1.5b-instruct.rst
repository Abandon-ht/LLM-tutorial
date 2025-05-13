`Qwen2.5-1.5B-Instruct <https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct>`_
============================================================================

Introduction
------------

Qwen2.5-1.5B-Instruct is part of the Qwen2.5 series, featuring instruction-tuned language models with 0.5 billion parameters. Key highlights of this model include:

- **Type**: Causal Language Model
- **Training Stage**: Pretraining & Post-training
- **Architecture**: Transformers with RoPE, SwiGLU, RMSNorm, Attention QKV bias, and tied word embeddings
- **Number of Parameters**: 1.54B (1.31B non-embedding)
- **Number of Layers**: 28
- **Number of Attention Heads (GQA)**: 12 for Q and 2 for KV
- **Context Length**: Full 32,768 tokens and generation up to 8,192 tokens

This model demonstrates significant improvements in instruction following, generating long texts, and understanding structured data. It supports multilingual capabilities across 29 languages, including English, Chinese, French, and more.

Available NPU Models
--------------------

Base Model
~~~~~~~~~~

qwen2.5-1.5B-ax630c
^^^^^^^^^^^^^^^^^^^

The **Base Model** provides a 128 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 128 context window

- 1,024 max output tokens

- ttft 1029.41ms

- avg-token/s 3.59

Long-Context Model
~~~~~~~~~~~~~~~~~~

qwen2.5-1.5B-p256-ax630c
^^^^^^^^^^^^^^^^^^^^^^^^

The **Long-Context Model** Compared to the **Base Model**, provides extended context capabilities, providing a 256 context window and a maximum of 1,024 output tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 256 context window

- 1,024 max output tokens

- ttft 3056.54ms

- avg-token/s 3.57

INT4 Quantized Model
~~~~~~~~~~~~~~~~~~~~

qwen2.5-1.5B-Int4-ax630c
^^^^^^^^^^^^^^^^^^^^^^^^

The **INT4 Quantized Model** compared to the **Base Model**, provides faster inference speed, offering a 128 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 128 context window

- 1,024 max output tokens

- ttft 1219.54ms

- avg-token/s 4.63