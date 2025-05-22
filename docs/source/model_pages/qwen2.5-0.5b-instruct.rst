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

Available NPU Models
--------------------

Base Model
~~~~~~~~~~

.. _qwen2.5-0.5b-prefill-20e:

qwen2.5-0.5B-prefill-20e
^^^^^^^^^^^^^^^^^^^^^^^^

The **Base Model** providing a 128 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 128 context window

- 1,024 max output tokens

- ttft 359.8ms

- avg-token/s 10.32

Install
"""""""

.. code-block:: shell

    apt install llm-model-qwen2.5-0.5b-prefill-20e

**Manual installation:** `Click here to download llm-model-qwen2.5-0.5b-prefill-20e <https://repo.llm.m5stack.com/m5stack-apt-repo/pool/jammy/ax630c/v0.2/llm-model-qwen2.5-0.5B-prefill-20e_0.2-m5stack1_arm64.deb>`_

Long-Context Model
~~~~~~~~~~~~~~~~~~

qwen2.5-0.5B-p256-ax630c
^^^^^^^^^^^^^^^^^^^^^^^^

The **Long-Context Model** Compared to the **Base Model**, it provides extended context capabilities, offering a 256 context window and a maximum of 1,024 output tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 256 context window

- 1,024 max output tokens

- ttft 1126.19ms

- avg-token/s 10.30

Install
"""""""

.. code-block:: shell

    apt install llm-model-qwen2.5-0.5b-p256-ax630c

**Manual installation:** `Click here to download llm-model-qwen2.5-0.5b-p256-ax630c <https://repo.llm.m5stack.com/m5stack-apt-repo/pool/jammy/ax630c/v0.4/llm-model-qwen2.5-0.5B-p256-ax630c_0.4-m5stack1_arm64.deb>`_

INT4 Quantized Model
~~~~~~~~~~~~~~~~~~~~

qwen2.5-0.5B-Int4-ax630c
^^^^^^^^^^^^^^^^^^^^^^^^

The **INT4 Quantized Model** compared to the **Base Model**, provides faster inference speed, offering a 128 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, Module LLM Kit

- 128 context window

- 1,024 max output tokens

- ttft 442.95ms

- avg-token/s 12.52

Install
"""""""

.. code-block:: shell

    apt install llm-model-qwen2.5-0.5b-int4-ax630c

**Manual installation:** `Click here to download llm-model-qwen2.5-0.5b-int4-ax630c <https://repo.llm.m5stack.com/m5stack-apt-repo/pool/jammy/ax630c/v0.4/llm-model-qwen2.5-0.5B-Int4-ax630c_0.4-m5stack1_arm64.deb>`_