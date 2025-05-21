`openbuddy-llama3.2-1b-v23.1-131k <https://huggingface.co/OpenBuddy/openbuddy-llama3.2-1b-v23.1-131k>`_
=======================================================================================================

Introduction
------------

OpenBuddy is a powerful open multilingual chatbot model aimed at global users, emphasizing conversational AI and seamless multilingual support for English, Chinese, and other languages.

Built upon Tii's Falcon model and Facebook's LLaMA model, OpenBuddy is fine-tuned to include an extended vocabulary, additional common characters, and enhanced token embeddings.
By leveraging these improvements and multi-turn dialogue datasets, OpenBuddy offers a robust model capable of answering questions and performing translation tasks across various languages.

Available NPU Models
--------------------

Base Model
~~~~~~~~~~

openbuddy-llama3.2-1B-ax630c
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The **Base Model** providing a 128 context window and a maximum output of 1,024 tokens.

**Support Platforms**: LLM630 Compute Kit, Module LLM, and Module LLM Kit

- 128 context window

- 1,024 max output tokens

- ttft 891.02ms

- avg-token/s 4.52

Install
"""""""

.. code-block:: shell

    apt install llm-model-openbuddy-llama3.2-1b-ax630c

**Manual installation:** `Click here to download llm-model-openbuddy-llama3.2-1b-ax630c <https://repo.llm.m5stack.com/m5stack-apt-repo/pool/jammy/ax630c/v0.2/llm-model-openbuddy-llama3.2-1B-ax630c_0.2-m5stack1_arm64.deb>`_