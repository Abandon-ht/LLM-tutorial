Text-to-Speech
==============

**Before using, make sure you have the latest software packages installed**

.. code-block:: shell

    apt install llm-melotts

.. note::

    This example is for the M5Stack Module LLM. It requires the M5Stack Module LLM to be connected to the M5Stack CoreS3 or M5Stack Basic.

    The example demonstrates how to use the M5ModuleLLM library to send a text to the LLM module and play synthesized audio.

    The example uses the USB serial port for communication. You can use any serial terminal program to send text to the module.

MeloTTS-English Example
-----------------------

**Before using, make sure you have the latest model packages installed**

.. code-block:: shell

    apt install llm-model-melotts-en-default

.. code-block:: cpp

    /*
    * SPDX-FileCopyrightText: 2024 M5Stack Technology CO LTD
    *
    * SPDX-License-Identifier: MIT
    */
    #include <Arduino.h>
    #include <M5Unified.h>
    #include <M5ModuleLLM.h>

    #define CommSerialPort Serial

    M5ModuleLLM module_llm;
    String tts_work_id;
    String language;
    String received_question;
    bool Input_completed;

    void setup()
    {
        M5.begin();
        M5.Display.setTextSize(2);
        M5.Display.setTextScroll(true);

        /* Init usb serial */
        CommSerialPort.begin(115200);

        language = "en_US";

        /* Init module serial port */
        int rxd = M5.getPin(m5::pin_name_t::port_c_rxd);
        int txd = M5.getPin(m5::pin_name_t::port_c_txd);
        Serial2.begin(115200, SERIAL_8N1, rxd, txd);

        /* Init module */
        module_llm.begin(&Serial2);

        /* Make sure module is connected */
        M5.Display.printf(">> Check ModuleLLM connection..\n");
        while (1) {
            if (module_llm.checkConnection()) {
                break;
            }
        }

        /* Reset ModuleLLM */
        M5.Display.printf(">> Reset ModuleLLM..\n");
        module_llm.sys.reset();

        /* Setup TTS module and save returned work id */
        M5.Display.printf(">> Initialize TTS..\n\n");
        m5_module_llm::ApiMelottsSetupConfig_t melotts_config;
        melotts_config.model = "melotts-en-default";
        tts_work_id          = module_llm.melotts.setup(melotts_config, "tts_setup", language);
        M5.Display.printf(">> Initialization completed..\n\n");
    }

    void loop()
    {
        Input_completed = false;
        if (CommSerialPort.available()) {
            while (CommSerialPort.available()) {
                char in_char = (char)CommSerialPort.read();
                received_question += in_char;

                if (received_question.endsWith("\r\n")) {
                    received_question.remove(received_question.length() - 2);
                    Input_completed = true;
                    break;
                }
            }
        }

        if (Input_completed) {
            /* Push text to TTS module and wait inference result */
            M5.Display.setTextColor(TFT_GREEN);
            M5.Display.printf("<< %s\n", received_question.c_str());
            M5.Display.setTextColor(TFT_YELLOW);
            M5.Display.printf(">> ");
            CommSerialPort.printf("<< \"%s\"\n", received_question.c_str());
            CommSerialPort.print(">> ");

            module_llm.tts.inference(tts_work_id, received_question.c_str(), 10000);

            /* Clear for next question */
            received_question.clear();

            M5.Display.println();
            CommSerialPort.println();
        }

        delay(20);
    }

class ApiMelotts
~~~~~~~~~~~~~~~~

.. code-block:: cpp

        struct ApiMelottsSetupConfig_t {
            String model              = "melotts-en-us";
            String response_format    = "sys.pcm";
            std::vector<String> input = {"tts.utf-8.stream"};
            bool enoutput             = false;
            bool enaudio              = true;
        };

- **model**: The model name. You can use "melotts-en-default" for English or "melotts-ja-jp" for Japanese.
- **enoutput**: If true, the TTS module will return the base64 encoding pcm data in utf-8 format.
- **enaudio**: If true, the TTS module will play the synthesized audio.

MeloTTS-Japanese Example
------------------------

**Before using, make sure you have the latest model packages installed**

.. code-block:: shell

    apt install llm-model-melotts-ja-jp

.. code-block:: cpp

    /*
    * SPDX-FileCopyrightText: 2024 M5Stack Technology CO LTD
    *
    * SPDX-License-Identifier: MIT
    */
    #include <Arduino.h>
    #include <M5Unified.h>
    #include <M5ModuleLLM.h>

    #define CommSerialPort Serial

    M5ModuleLLM module_llm;
    String tts_work_id;
    String language;
    String received_question;
    bool Input_completed;

    void setup()
    {
        M5.begin();
        M5.Display.setTextSize(2);
        M5.Display.setTextScroll(true);
        M5.Display.setFont(&fonts::efontJA_12);

        /* Init usb serial */
        CommSerialPort.begin(115200);

        language = "ja_JP";

        /* Init module serial port */
        int rxd = M5.getPin(m5::pin_name_t::port_c_rxd);
        int txd = M5.getPin(m5::pin_name_t::port_c_txd);
        Serial2.begin(115200, SERIAL_8N1, rxd, txd);

        /* Init module */
        module_llm.begin(&Serial2);

        /* Make sure module is connected */
        M5.Display.printf(">> Check ModuleLLM connection..\n");
        while (1) {
            if (module_llm.checkConnection()) {
                break;
            }
        }

        /* Reset ModuleLLM */
        M5.Display.printf(">> Reset ModuleLLM..\n");
        module_llm.sys.reset();

        /* Setup TTS module and save returned work id */
        M5.Display.printf(">> Initialize TTS..\n\n");
        m5_module_llm::ApiMelottsSetupConfig_t melotts_config;
        melotts_config.model = "melotts-ja-jp";
        tts_work_id          = module_llm.melotts.setup(melotts_config, "tts_setup", language);
        M5.Display.printf(">> Initialization completed..\n\n");
    }

    void loop()
    {
        Input_completed = false;
        if (CommSerialPort.available()) {
            while (CommSerialPort.available()) {
                char in_char = (char)CommSerialPort.read();
                received_question += in_char;

                if (received_question.endsWith("\r\n")) {
                    received_question.remove(received_question.length() - 2);
                    Input_completed = true;
                    break;
                }
            }
        }

        if (Input_completed) {
            /* Push text to TTS module and wait inference result */
            M5.Display.setTextColor(TFT_GREEN);
            M5.Display.printf("<< %s\n", received_question.c_str());
            M5.Display.setTextColor(TFT_YELLOW);
            M5.Display.printf(">> ");
            CommSerialPort.printf("<< \"%s\"\n", received_question.c_str());
            CommSerialPort.print(">> ");

            module_llm.tts.inference(tts_work_id, received_question.c_str(), 10000);

            /* Clear for next question */
            received_question.clear();

            M5.Display.println();
            CommSerialPort.println();
        }

        delay(20);
    }