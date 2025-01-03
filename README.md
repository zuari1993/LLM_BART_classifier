# Zero-Shot Text Classification with Hugging Face Transformers

This repository contains a Jupyter Notebook for zero-shot text classification using models like BART and RoBERTa from the Hugging Face Transformers library. It provides a streamlined approach to classify textual data into pre-defined categories without requiring extensive model retraining.

## Features
- All the above models are lightweight and can run efficiently on edge devices.
- Zero-Shot Classification
  - Enables categorization of text into user-defined labels without additional fine-tuning of the model.
- Model Flexibility: Supports various models, including:

#### `facebook/bart-large-mnli`
- Robust, pretrained for natural language inference (NLI).
- Slower but robust; works out of the box.
- Pretrained on MNLI.
- Initialization Time: ~50 seconds.
- Inference Time: ~4 seconds per classification.
- Model Size: 420 million parameters.
- Ideal for NLI classification tasks.
- [Model Details](https://huggingface.co/facebook/bart-large-mnli)

#### `cross-encoder/nli-roberta-base`
- Efficient with faster initialization.
- Initialization Time: ~4 seconds.
- Inference Time: ~0.1 seconds per classification.
- Pretrained on MNLI.
- Model Size: 120 million parameters.
- Balanced performance for zero-shot tasks.
- [Model Details](https://huggingface.co/cross-encoder/nli-roberta-base)

#### `TinyBERT_General_4L_312D`
- Lightweight and suitable for rapid inference.
- Fastest among supported models.
- Initialization Time: ~0.4 seconds.
- Inference Time: <0.1 seconds per classification.
- Pretrained on MNLI but requires fine-tuning for optimal results.
- Model Size: 14.5 million parameters.
- Ideal for edge devices.
- [Model Details](https://huggingface.co/huawei-noah/TinyBERT_General_4L_312D)



## Models Overview

| Model                     | Parameters (Millions) | Initialization Time (s) | Inference Time (s) | Notes                                   | Link                                                                 |
|---------------------------|-----------------------|-------------------------|---------------------|-----------------------------------------|----------------------------------------------------------------------|
| `facebook/bart-large-mnli` | 420                  | ~50                    | ~4                  | Robust for NLI tasks, works out of the box | [View Model](https://huggingface.co/facebook/bart-large-mnli)       |
| `cross-encoder/nli-roberta-base` | 120          | ~4                     | ~0.1                | Balanced performance for zero-shot tasks | [View Model](https://huggingface.co/cross-encoder/nli-roberta-base) |
| `TinyBERT_General_4L_312D` | 14.5                | ~0.4                   | < 0.1               | Lightweight, requires fine-tuning        | [View Model](https://huggingface.co/huawei-noah/TinyBERT_General_4L_312D) |

## Files
- The `training_data_generator.ipynb` uses Gemini API calls to generate ~100 user like prompts and their classification category. This can be used as validation set / test set.
- The `LLM_BART_classifier.ipynb` file runs any of the above 3 model locally to classify these 100 prompts and computes the classification accuracy
