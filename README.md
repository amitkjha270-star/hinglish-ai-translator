# English to Hinglish AI Translator 🚀

## 1. The Model & Training Settings
* **Base Model:** Gemma 4 E2B
* **Method:** Low-Rank Adaptation (LoRA) via Unsloth
* **Parameters:** LoRA Rank: 8, Training Steps: 150, Learning Rate: 2e-4, Optimizer: adamw_8bit.
* **Weights:** The trained adapters are available in this repository as `gemma_4_lora.zip`.

## 2. Dataset Description
* **Source:** `ai4bharat/IndicCMix` (Hugging Face)
* **Format:** Instruction-response pairs mapping formal `english` to `romanized_casual` Hindi.
* **Size & Split:** 104,770 training examples and 30 isolated test examples. The split was randomized with a 95/5 ratio to prevent data leakage.

## 3. Comparative Analysis
The models were evaluated against the 30 test examples using the **chrF score** metric, which is optimal for transliterated text with non-standardized spellings.
* **Plain Gemma (Baseline):** 42.3 chrF
* **Fine-Tuned Gemma:** 71.8 chrF
* **Improvement:** +29.5 points

## 4. Discussion: Where Fine-Tuning Helped
* **Tone & Vocabulary:** The baseline model defaulted to formal Hindi scripts or pure English explanations. Fine-tuning forced the model to exclusively output Romanized Hinglish.
* **Code-Mixing:** The fine-tuned model successfully learned the phonetic patterns of casual chat (e.g., translating "daily problem" to "roz ki tension").
* **Application:** The project features a Gradio web interface with dynamic vibe selection (Standard, Gen-Z Slang, Polite) and Whisper AI voice input integration.
