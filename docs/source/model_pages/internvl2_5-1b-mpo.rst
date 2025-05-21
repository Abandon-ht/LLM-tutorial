`InternVL2_5-1B-MPO <https://huggingface.co/OpenGVLab/InternVL2_5-1B-MPO>`_
===========================================================================

Introduction
------------

InternVL 2.5, an advanced multimodal large language model (MLLM) series that builds upon InternVL 2.0, maintaining its core model architecture while introducing significant enhancements in training and testing strategies as well as data quality.

Available NPU Models
--------------------

Base Model
~~~~~~~~~~

internvl2.5-1b-364-ax630c
^^^^^^^^^^^^^^^^^^^^^^^^^

The **Base Model** providing a 256 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 256 context window

- 1,024 max output tokens

- ttft 1117.27ms

- avg-token/s 10.56

- Image encoding size 364*364

- Image encoding time 1164.61ms

Install
"""""""

.. code-block:: shell

    apt install llm-model-internvl2.5-1b-364-ax630c

**Manual installation:** `Click here to download llm-model-internvl2.5-1b-364-ax630c <https://repo.llm.m5stack.com/m5stack-apt-repo/pool/jammy/ax630c/v0.4/llm-model-internvl2.5-1B-364-ax630c_0.4-m5stack1_arm64.deb>`_