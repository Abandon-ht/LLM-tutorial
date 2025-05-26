API reference
=============

This section provides a reference for the Arduino API used in the examples. It includes details on the functions, classes, and methods available for use in your Arduino projects.

Keyword Spotting
----------------

class ApiKws
~~~~~~~~~~~~

struct ApiKwsSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    struct ApiKwsSetupConfig_t {
        String kws                = "HELLO";
        String model              = "sherpa-onnx-kws-zipformer-gigaspeech-3.3M-2024-01-01";
        String response_format    = "kws.bool";
        std::vector<String> input = {"sys.pcm"};
        bool enoutput             = true;
        bool enaudio              = true;
    };

- **kws**: The wake-up keyword to listen for. Must be capitalized.
- **model**: The model to use for keyword spotting. Default is "sherpa-onnx-kws-zipformer-gigaspeech-3.3M-2024-01-01". 

  You can also use "**sherpa-onnx-kws-zipformer-gigaspeech-3.3M-2024-01-01-en**" for English or "**sherpa-onnx-kws-zipformer-wenetspeech-3.3m-2024-01-01**" for Chinese.

- **enaudio**: If true, the KWS module will play the wake-up audio. Default is true.

function setup
^^^^^^^^^^^^^^

.. code-block:: cpp

    String setup(ApiKwsSetupConfig_t config = ApiKwsSetupConfig_t(), String request_id = "kws_setup",
                 String language = "en_US");

- **config**: The configuration for the KWS module. You can use the ApiKwsSetupConfig_t to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **language**: The language for the KWS module. You can use "en_US" for English.
- **return**: The work ID for the KWS module setup. This ID is used for subscriptions in other modules.

Text-to-speech
--------------

class ApiMelotts
~~~~~~~~~~~~~~~~

struct ApiMelottsSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    struct ApiMelottsSetupConfig_t {
        String model              = "melotts-en-us";
        String response_format    = "sys.pcm";
        std::vector<String> input = {"tts.utf-8.stream"};
        bool enoutput             = false;
        bool enaudio              = true;
    };

- **model**: The model name. You can use "**melotts-en-default**" for English or "**melotts-ja-jp**" for Japanese.
- **response_format**: The response format for the TTS module. You can use "**sys.pcm**" for PCM audio data. The generated audio can be played through the onboard speakers.
- **input**: The input format for the TTS module. You can use "**tts.utf-8.stream**" for UTF-8 encoded text streaming input.
- **enoutput**: If true, the TTS module will return the base64 encoding pcm data in utf-8 format. Default is false.
- **enaudio**: If true, the TTS module will play the synthesized audio. Default is true.

function setup
^^^^^^^^^^^^^^

.. code-block:: cpp

    String setup(ApiMelottsSetupConfig_t config = ApiMelottsSetupConfig_t(), 
                 String request_id = "melotts_setup",
                 String language = "en_US");

- **config**: The configuration for the TTS module. You can use the ApiMelottsSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **language**: The language for the TTS module. You can use "en_US" for English or "ja_JP" for Japanese.
- **return**: The work ID for the TTS module. You need to use this work ID for the inference function.

function inference
^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    int inference(String work_id, String input, uint32_t timeout = 0, String request_id = "tts_inference");

- **work_id**: The work ID for the TTS module. You need to use the work ID returned by the setup function.
- **input**: The text to be synthesized. You can use any string as the input.
- **timeout**: The timeout for the inference. You can use 0 for no timeout.
- **request_id**: The request ID for the inference. You can use any string as the request ID.

Transcription
-------------

class ApiWhisper
~~~~~~~~~~~~~~~~

struct ApiWhisperSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Before using, make sure you have the latest model packages installed on ModuleLLM.**

.. code-block:: shell

    apt install llm-model-whisper-tiny llm-model-silero-vad llm-model-sherpa-onnx-kws-zipformer-gigaspeech-3.3m-2024-01-01

.. tip::

    For more information about this model :ref:`see the details <whisper-tiny>`.

.. code-block:: cpp

        struct ApiWhisperSetupConfig_t {
            String model              = "whisper-tiny";
            String response_format    = "asr.utf-8";
            String language           = "en";
            std::vector<String> input = {"sys.pcm"};
            bool enoutput             = true;
        };

- "**model**: The model name. default is "whisper-tiny". You can use "whisper-base" or "whisper-small" for larger models.
- "**response_format** is the response format, default is "asr.utf-8". whisper only supports non-streaming response.
- **enoutput**: If true, the Whisper module will return the transcribe text in utf-8 format.

function setup
^^^^^^^^^^^^^^
.. code-block:: cpp

    String setup(ApiWhisperSetupConfig_t config = ApiWhisperSetupConfig_t(), String request_id = "asr_setup",
                 String language = "en_US");

- **config**: The configuration for the Whisper module. You can use the ApiWhisperSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **language**: The language for the Whisper module. You can use "en_US" for English or "ja_JP" for Japanese.
- **return**: The work ID for the Whisper module. You need to use this work ID for the inference function.  

Voice activity detection
------------------------

class ApiVad
~~~~~~~~~~~~

struct ApiVadSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    struct ApiVadSetupConfig_t {
        String model              = "silero-vad";
        String response_format    = "vad.bool";
        std::vector<String> input = {"sys.pcm"};
        bool enoutput             = true;
    };

- **model**: The model name for voice activity detection. Default is "silero-vad".
- **response_format**: The response format for the VAD module. Default is "vad.bool", which returns a boolean indicating whether speech is detected.
- **input**: The input format for the VAD module. Default is {"sys.pcm"}, which means it will process PCM audio data.
- **enoutput**: If true, the VAD module will return the boolean result in the response. Default is true.

Automatic Speech Recognition
----------------------------

class ApiAsr
~~~~~~~~~~~~

struct ApiAsrSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: cpp

    struct ApiAsrSetupConfig_t {
        String model              = "sherpa-ncnn-streaming-zipformer-20M-2023-02-17";
        String response_format    = "asr.utf-8.stream";
        std::vector<String> input = {"sys.pcm"};
        bool enoutput             = true;
        bool enkws                = true;
        float rule1               = 2.4;
        float rule2               = 1.2;
        float rule3               = 30.0;
    };

- **model**: The model name for automatic speech recognition. Default is "sherpa-ncnn-streaming-zipformer-20M-2023-02-17". You can use "sherpa-ncnn-streaming-zipformer-20M-2023-02-17-en" for English or "sherpa-ncnn-streaming-zipformer-wenetspeech-20M-2023-02-17" for Chinese.
- **response_format**: The response format for the ASR module. Default is "asr.utf-8.stream", which returns the transcribed text in a streaming format.
- **input**: The input format for the ASR module. Default is {"sys.pcm"}, which means it will process PCM audio data.
- **enoutput**: If true, the ASR module will return the transcribed text in utf-8 format. Default is true.
- **enkws**: If true, the ASR module will enable keyword spotting. Default is true.
- **rule1**, **rule2**, **rule3**:

function setup
^^^^^^^^^^^^^^

.. code-block:: cpp

    String setup(ApiAsrSetupConfig_t config = ApiAsrSetupConfig_t(), String request_id = "asr_setup",
                String language = "en_US");

- **config**: The configuration for the ASR module. You can use the ApiAsrSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **language**: The language for the ASR module. You can use "en_US" for English or "zh_CN" for Chinese.
- **return**: The work ID for the ASR module. You need to use this work ID for the inference function.

Large Language Model
--------------------

class ApiLlm
~~~~~~~~~~~~

struct ApiLLMSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    struct ApiLlmSetupConfig_t {
        String prompt;
        String model              = "qwen2.5-0.5B-prefill-20e";
        String response_format    = "llm.utf-8.stream";
        std::vector<String> input = {"llm.utf-8.stream"};
        bool enoutput             = true;
        bool enkws                = true;
        int max_token_len         = 127;
        // int max_token_len      = 512;
    };

- **prompt**: The prompt for the LLM model. The prompt is used to initialize the model and can be used to set the context for the model.
- **model**: The model name. You can use "qwen2.5-0.5B-prefill-20e" for the Qwen2.5 model.
- **response_format**: The response format.
- **max_token_len**: The maximum number of tokens to generate. The default is 127. You can set it to 512 for larger models.

function setup
^^^^^^^^^^^^^^

.. code-block:: cpp

    String setup(ApiLlmSetupConfig_t config = ApiLlmSetupConfig_t(), String request_id = "llm_setup");

- **config**: The configuration for the LLM model. You can use the ApiLLMSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **return**: The work ID for the LLM model. You need to use this work ID for the inference function.

function inference
^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    int inference(String work_id, String input, String request_id = "llm_inference");

- **work_id**: The work ID for the LLM model. You need to use the work ID returned by the setup function.
- **input**: The input text for the LLM model. You can use any string as the input.
- **request_id**: The request ID for the inference. You can use any string as the request ID.

Visual Language Model
---------------------

class ApiVlm
~~~~~~~~~~~~

struct ApiVlmSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    struct ApiVlmSetupConfig_t {
        String prompt;
        String model              = "internvl2.5-1B-ax630c";
        String response_format    = "vlm.utf-8.stream";
        std::vector<String> input = {"vlm.utf-8.stream"};
        bool enoutput             = true;
        bool enkws                = true;
        // int max_token_len         = 127;
        int max_token_len = 255;
    };

- **prompt**: The prompt for the VLM model. The prompt is used to initialize the model and can be used to set the context for the model.
- **model**: The model name. You can use "internvl2.5-1B-ax630c" for the InternVL2.5 model.
- **response_format**: The response format.
- **max_token_len**: The maximum number of tokens to generate. The default is 255. You can set it to 512 for larger models.

function setup
^^^^^^^^^^^^^^

.. code-block:: cpp

    String setup(ApiVlmSetupConfig_t config = ApiVlmSetupConfig_t(), String request_id = "vlm_setup");

- **config**: The configuration for the VLM model. You can use the ApiVlmSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **return**: The work ID for the VLM model. You need to use this work ID for the inference function.

function inference
^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    int inference(String work_id, String input, String request_id = "vlm_inference");

- **work_id**: The work ID for the VLM model. You need to use the work ID returned by the setup function.
- **input**: The input text for the VLM model. You can use any string as the input.
- **request_id**: The request ID for the inference. You can use any string as the request ID.

Vision
------

class ApiDepthAnything
~~~~~~~~~~~~~~~~~~~~~~

struct ApiDepthAnythingSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: cpp

    struct ApiDepthAnythingSetupConfig_t {
        String model              = "depth-anything-ax630c";
        String response_format    = "jpeg.base64.stream";
        std::vector<String> input = {"depth_anything.jpeg.raw"};
        bool enoutput             = true;
    };

- **model**: The model name for depth estimation. Default is "depth-anything-ax630c".
- **response_format**: The response format for the depth estimation module. Default is "jpeg.base64.stream", which returns the depth map as a JPEG image in base64 format.
- **input**: The input format for the depth estimation module. Default is {"depth_anything.jpeg.raw"}, which means it will process raw JPEG images.
- **enoutput**: If true, the depth estimation module will return the depth map in base64 format. Default is true.

function setup
^^^^^^^^^^^^^^

.. code-block:: cpp

    String setup(ApiDepthAnythingSetupConfig_t config = ApiDepthAnythingSetupConfig_t(),
                String request_id = "depth_anything_setup");

- **config**: The configuration for the depth estimation module. You can use the ApiDepthAnythingSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **return**: The work ID for the depth estimation module. You need to use this work ID for the inference function.

function inference
^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    int inference(String& work_id, uint8_t* input, size_t& raw_len, String request_id = "depth_anything_inference");

- **work_id**: The work ID for the depth estimation module. You need to use the work ID returned by the setup function.
- **input**: The input image for depth estimation. You can use the path to the raw JPEG image.
- **raw_len**: The length of the raw image data.
- **request_id**: The request ID for the inference. You can use any string as the request ID.

class ApiYolo
~~~~~~~~~~~~~

struct ApiYoloSetupConfig_t
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    struct ApiYoloSetupConfig_t {
        String model              = "yolo11n";
        String response_format    = "yolo.box.stream";
        std::vector<String> input = {"yolo.jpeg.base64"};
        bool enoutput             = true;
    };

- **model**: The model name for object detection. Default is "yolo11n".
- **response_format**: The response format for the object detection module. Default is "yolo.box.stream", which returns the detected bounding boxes in a streaming format.
- **input**: The input format for the object detection module. Default is {"yolo.jpeg.base64"}, which means it will process JPEG images in base64 format.
- **enoutput**: If true, the object detection module will return the detected bounding boxes in the response. Default is true.

function setup
^^^^^^^^^^^^^^
.. code-block:: cpp

    String setup(ApiYoloSetupConfig_t config = ApiYoloSetupConfig_t(), String request_id = "yolo_setup");

- **config**: The configuration for the object detection module. You can use the ApiYoloSetupConfig_t struct to set the model name and other parameters.
- **request_id**: The request ID for the setup. You can use any string as the request ID.
- **return**: The work ID for the object detection module. You need to use this work ID for the inference function.

function inference
^^^^^^^^^^^^^^^^^^

.. code-block:: cpp

    int inference(String& work_id, uint8_t* input, size_t& raw_len, String request_id = "yolo_inference");

- **work_id**: The work ID for the object detection module. You need to use the work ID returned by the setup function.
- **input**: The input image for object detection. You can use the path to the raw JPEG image.
- **raw_len**: The length of the raw image data.
- **request_id**: The request ID for the inference. You can use any string as the request ID.