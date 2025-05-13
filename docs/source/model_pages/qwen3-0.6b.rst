`Qwen3-0.6B <https://huggingface.co/Qwen/Qwen3-0.6B>`_
================================================

Introduction
------------

Qwen3 is the latest large language model in the Qwen series, offering both dense and Mixture-of-Experts (MoE) architectures. It features seamless switching between thinking and non-thinking modes, enhanced reasoning and instruction-following abilities, superior human preference alignment for engaging conversations, strong agent capabilities for tool integration, and support for over 100 languages with excellent multilingual performance.

- **Type**: Causal Language Model
- **Training Stage**: Pretraining & Post-training
- **Number of Parameters**: 0.6B (0.44B non-embedding)
- **Number of Layers**: 28
- **Number of Attention Heads (GQA)**: 16 for Q, 8 for KV
- **Context Length**: 32,768

qwen3-0.6B-ax630c
----------------

- 128 context window

- 1,024 max output tokens

- ttft 361.81ms

- avg-token/s 10.28

**base model** suitable for the LLM630 Compute Kit, Module LLM, and Module LLM Kit, providing a 128 context window and a maximum output of 1,024 tokens.