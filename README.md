
# ParagraphAI: Prompt-to-Completion Text Generation Using GPT-2

This project demonstrates how to fine-tune a pre-trained GPT-2 language model using supervised learning on a custom dataset consisting of writing prompts and their corresponding paragraph completions.

## 📘 Overview

- **Model**: Fine-tuned GPT-2 (`openai-community/gpt2`)
- **Dataset**: Text paragraphs separated by `---`, structured into `prompt → completion`
- **Training Framework**: Hugging Face Transformers, Datasets, and PyTorch
- **Environment**: Google Colab

## 📁 Directory Structure

```

ParagraphAI/
├── Paragraphs.txt                  # Original raw dataset
├── data.jsonl                      # (Optional) Exported JSONL format
├── prompt\_completion\_dataset.csv  # Final formatted dataset
├── training\_log.csv               # Training metrics logged by Trainer
├── my\_finetuned\_gpt2/             # Folder with saved model and tokenizer
├── ParagraphAI.ipynb              # Complete notebook with training and inference

````

## 🚀 Features

- Converts raw `.txt` data into structured prompt/completion pairs
- Tokenizes and prepares data for supervised fine-tuning
- Logs training progress and loss values
- Saves model and tokenizer locally for future inference
- **Three methods** of inference:
  1. Static prompt in code
  2. Dynamic prompt using Python’s `input()`
  3. GUI interface with Gradio

## 🧠 Model Training Summary

- **Tokenizer**: AutoTokenizer from Hugging Face (`gpt2`)
- **Tokenized Length**: Max 512 tokens
- **Batch Size**: 2
- **Epochs**: 3
- **Trainer API**: Hugging Face Trainer with `TrainingArguments`
- **WandB**: Disabled for simplicity (`os.environ["WANDB_DISABLED"] = "true"`)

## 💡 Inference Options

### 1. Hardcoded Prompt
```python
print(generate_text(prompt="How the traffic jam is Harming us?"))
````

### 2. Dynamic Input

```python
prompt = input("Enter your prompt: ")
print(generate_text(prompt))
```

### 3. Gradio GUI

```python
import gradio as gr
interface = gr.Interface(fn=generate_text, inputs="text", outputs="text", title="ParagraphAI Generator")
interface.launch()
```

## 🧪 Results

* Training converged with decreasing loss per step
* The model successfully generates contextually relevant paragraphs
* Output examples are available in the notebook screenshots

## 📦 Installation

```bash
pip install transformers datasets pandas gradio
```

## 📈 Logs

Training logs are saved to:

```
/ParagraphAI/training_log.csv
```

## ✅ Improvements

* Interactive prompt interface (Gradio)
* Dynamic user input with `input()`
* Optional: JSONL export for Hugging Face upload

## 📜 License

This project is released under the MIT License.

---

