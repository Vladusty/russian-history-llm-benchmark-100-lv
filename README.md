# Russian History LLM Benchmark (100 Questions, LV)

A compact benchmark for evaluating Large Language Models (LLMs) on factual Russian history tasks.

The dataset contains **100 multiple-choice questions** translated into Latvian.  
Questions are adapted from the Russian Unified State Exam (ЕГЭ or EGE), specifically the **matching-task format**.  
Each sub-item (A/B/C/D) is converted into a **standalone single-choice question**, identified using a unique `subref`.

---

## Contents

This repository includes:

- **Dataset**: `russian_history_unified_state_exam_matching_task_100_lv.json`  
- **Evaluation notebook**: `russian_history_llm_evaluation.ipynb` [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/16ZqljMNNltYmrNpMXJimMYwNi4o0daMM?usp=sharing)
- **Evaluation pipeline**: prompt construction, output parsing, metrics  
- **Precomputed results** for several models (Gemma, Tilde, Llama, Mistral, GPT-4o-mini, Grok, Haiku, Qwen, etc.)

The benchmark is intended to measure:
- factual accuracy,
- reliability under strict “single-digit output” constraints,
- model performance on non-Western, historically specific material.

---

## Dataset Format

Each JSON entry contains:

- `ref` — original EGE task ID  
- `subref` — unique sub-question ID (A/B/C/D)  
- `question` — Latvian translation of the historical question  
- `options` — six answer choices (1–6)  
- `answer` — correct option number  
- `source_url` — original FIPI entry  

The dataset is fully human-checked to ensure correctness of translation and content.

---

## Evaluation Notebook

The notebook `russian_history_llm_evaluation.ipynb` provides:

- evaluation over local LUMII models and OpenRouter models  
- strict prompt formatting that forces **digit-only answers**  
- deterministic output parsing (skipped cases reported explicitly)  
- metrics:
  - accuracy  
  - macro-precision  
  - macro-recall  
  - macro-F1  

A verbose mode is available for inspecting raw model outputs.

---

📊 Model Evaluation Results

| Model                           | Total | Evaluated | Correct | Skipped | Accuracy | Macro Precision | Macro Recall | Macro F1 |
| ------------------------------- | ----- | --------- | ------- | ------- | -------- | --------------- | ------------ | -------- |
| google/gemma-2-27b-it           | 100   | 100       | 74      | 0       | 0.74 | 0.7426          | 0.7296       | 0.7288   |
| google/gemma-2-27b              | 100   | 100       | 62      | 0       | 0.62 | 0.6872          | 0.6255       | 0.6175   |
| TildeAI/TildeOpen-30b           | 100   | 100       | 79      | 0       | 0.79 | 0.8063          | 0.7800       | 0.7769   |
| meta-llama/llama-3-8b-instruct  | 100   | 100       | 32      | 0       | 0.32 | 0.3708          | 0.3185       | 0.3198   |
| qwen/qwen-2.5-7b-instruct       | 100   | 100       | 39      | 0       | 0.39 | 0.4075          | 0.3739       | 0.3682   |
| mistralai/mixtral-8x7b-instruct | 100   | 100       | 37      | 0       | 0.37 | 0.4357          | 0.3751       | 0.3811   |
| mistralai/mistral-nemo          | 100   | 100       | 48      | 0       | 0.48 | 0.5405          | 0.4799       | 0.4711   |
| anthropic/claude-3-haiku        | 100   | 100       | 87      | 0       | 0.87 | 0.8789          | 0.8627       | 0.8681   |
| openai/gpt-4o-mini              | 100   | 100       | 87      | 0       | 0.87 | 0.8684          | 0.8633       | 0.8633   |
| x-ai/grok-4-fast                | 100   | 100       | 97      | 0       | 0.97 | 0.9731          | 0.9731       | 0.9731   |


---


## License

- **Code**: MIT License  
- **Dataset (Latvian translation and formatting)**: MIT License  

Original question concepts come from publicly available materials of the Russian Unified State Exam (ЕГЭ):  
https://ege.fipi.ru/bank/index.php?proj=068A227D253BA6C04D0C832387FD0D89

---
