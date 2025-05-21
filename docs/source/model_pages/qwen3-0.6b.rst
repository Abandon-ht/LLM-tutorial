`Qwen3-0.6B <https://huggingface.co/Qwen/Qwen3-0.6B>`_
======================================================

Introduction
------------

Qwen3 is the latest large language model in the Qwen series, offering both dense and Mixture-of-Experts (MoE) architectures. It features seamless switching between thinking and non-thinking modes, enhanced reasoning and instruction-following abilities, superior human preference alignment for engaging conversations, strong agent capabilities for tool integration, and support for over 100 languages with excellent multilingual performance.

- **Type**: Causal Language Model
- **Training Stage**: Pretraining & Post-training
- **Number of Parameters**: 0.6B (0.44B non-embedding)
- **Number of Layers**: 28
- **Number of Attention Heads (GQA)**: 16 for Q, 8 for KV
- **Context Length**: 32,768

Available NPU Models
--------------------

Base Model
~~~~~~~~~~

qwen3-0.6B-ax630c
^^^^^^^^^^^^^^^^^

The **base model** providing a 128 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 128 context window

- 1,024 max output tokens

- ttft 361.81ms

- avg-token/s 10.28

Install
"""""""

.. code-block:: shell

    apt install llm-model-qwen3-0.6b-ax630c

**Manual installation:** `Click here to download llm-model-qwen3-0.6b-ax630c <https://repo.llm.m5stack.com/m5stack-apt-repo/pool/jammy/ax630c/v0.4/llm-model-qwen3-0.6B-ax630c_0.4-m5stack1_arm64.deb>`_