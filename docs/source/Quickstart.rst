Quickstart
==========

Getting starte with your ModuleLLM Kit. Please be sure to follow the steps below in order.

Software Upgrade
----------------

Before use, please to the `Software Upgrade <https://docs.m5stack.com/en/guide/llm/llm/image>`_ tutorial to add the M5Stack apt repository info and update the index.


Get a list of available software
--------------------------------

.. code-block:: shell

    apt update

    apt list | grep llm

.. code-block:: shell

    llm-asr/stable,now 1.6 arm64 [installed]
    llm-audio/stable 1.6 arm64 [upgradable from: 1.3]
    llm-camera/stable 1.8 arm64 [upgradable from: 1.3]
    llm-depth-anything/stable 1.6 arm64
    llm-kws/stable,now 1.7 arm64 [installed]
    llm-llm/stable,now 1.8 arm64 [installed]
    llm-melotts-zh-cn/now 0.2 arm64 [installed,local]
    llm-melotts/stable,now 1.7 arm64 [installed]
    llm-openai-api/stable,now 1.7 arm64 [installed]
    llm-qwen2.5-0.5b-prefill-20e/now 0.2 arm64 [installed,local]
    llm-single-speaker-english-fast/now 0.2 arm64 [installed,local]
    llm-single-speaker-fast/now 0.2 arm64 [installed,local]
    llm-skel/stable 1.5 arm64 [upgradable from: 1.3]
    llm-sys/stable,now 1.6 arm64 [installed]
    llm-tts/stable 1.6 arm64 [upgradable from: 1.3]
    llm-vad/stable,now 1.6 arm64 [installed]
    llm-vlm/stable 1.7 arm64 [upgradable from: 1.3]
    llm-whisper/stable,now 1.7 arm64 [installed]
    llm-yolo/stable 1.8 arm64 [upgradable from: 1.3]

Get a list of available model
-----------------------------

.. code-block:: shell

    apt list | grep llm-model

.. code-block:: shell

    llm-model-audio-en-us/stable,now 0.2 arm64 [installed]
    llm-model-audio-zh-cn/stable,now 0.2 arm64 [installed]
    llm-model-deepseek-r1-1.5b-ax630c/stable 0.3 arm64
    llm-model-deepseek-r1-1.5b-p256-ax630c/stable 0.4 arm64
    llm-model-depth-anything-ax630c/stable 0.4 arm64
    llm-model-internvl2.5-1b-364-ax630c/stable 0.4 arm64
    llm-model-internvl2.5-1b-ax630c/stable 0.4 arm64
    llm-model-llama3.2-1b-p256-ax630c/stable 0.4 arm64
    llm-model-llama3.2-1b-prefill-ax630c/stable 0.2 arm64
    llm-model-melotts-en-default/stable,now 0.5 arm64 [installed]
    llm-model-melotts-en-us/stable 0.5 arm64
    llm-model-melotts-ja-jp/stable,now 0.5 arm64 [installed]
    llm-model-melotts-zh-cn/stable 0.5 arm64
    llm-model-openbuddy-llama3.2-1b-ax630c/stable 0.2 arm64
    llm-model-qwen2.5-0.5b-int4-ax630c/stable 0.4 arm64
    llm-model-qwen2.5-0.5b-p256-ax630c/stable 0.4 arm64
    llm-model-qwen2.5-0.5b-prefill-20e/stable 0.2 arm64
    llm-model-qwen2.5-1.5b-ax630c/stable 0.3 arm64
    llm-model-qwen2.5-1.5b-int4-ax630c/stable 0.4 arm64
    llm-model-qwen2.5-1.5b-p256-ax630c/stable 0.4 arm64
    llm-model-qwen2.5-coder-0.5b-ax630c/stable 0.2 arm64
    llm-model-qwen3-0.6b-ax630c/stable 0.4 arm64
    llm-model-sherpa-ncnn-streaming-zipformer-20m-2023-02-17/stable,now 0.2 arm64 [installed]
    llm-model-sherpa-ncnn-streaming-zipformer-zh-14m-2023-02-23/stable,now 0.2 arm64 [installed]
    llm-model-sherpa-onnx-kws-zipformer-gigaspeech-3.3m-2024-01-01/stable,now 0.3 arm64 [installed]
    llm-model-sherpa-onnx-kws-zipformer-wenetspeech-3.3m-2024-01-01/stable,now 0.3 arm64 [installed]
    llm-model-silero-vad/stable,now 0.4 arm64 [installed]
    llm-model-single-speaker-english-fast/stable 0.3 arm64
    llm-model-single-speaker-fast/stable 0.3 arm64
    llm-model-smolvlm-256m-ax630c/stable 0.4 arm64
    llm-model-smolvlm-500m-ax630c/stable 0.4 arm64
    llm-model-whisper-base/stable 0.4 arm64
    llm-model-whisper-small/stable 0.4 arm64
    llm-model-whisper-tiny/stable,now 0.4 arm64 [installed]
    llm-model-yolo11n-hand-pose/stable 0.3 arm64
    llm-model-yolo11n-pose/stable,now 0.3 arm64 [installed]
    llm-model-yolo11n-seg/stable,now 0.3 arm64 [installed]
    llm-model-yolo11n/stable,now 0.2 arm64 [installed]

Update the latest software package
----------------------------------

.. code-block:: shell

    apt install lib-llm llm-sys