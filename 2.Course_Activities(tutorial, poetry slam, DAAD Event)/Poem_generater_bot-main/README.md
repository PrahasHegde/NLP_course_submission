# PoetBot 📜✨

**A beautiful, offline AI poetry generator living in your terminal.**

Silicon Muse is a Python-based Terminal User Interface (TUI) that uses a local LLM (Large Language Model) to generate poetry on the fly. It features a cyberpunk-aesthetic interface, real-time typing effects, and runs entirely offline without an internet connection.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Rich-purple)
![Model](https://img.shields.io/badge/Model-TinyLlama_GGUF-orange)

## 📂 Project Structure

This repository contains two variations of the Muse:

1.  **`main.py` (Standard Edition):** Takes a single emotion, topic, or theme and generates a deep, atmospheric poem.
2.  **`muse.py` (The Triad Edition):** Challenges the AI to weave exactly **three specific words** (e.g., "Neon, Rain, Silence") into a cohesive poem.

## 🚀 Features

* **100% Offline:** Runs locally on your machine using `llama-cpp-python`. No API keys or internet required after setup.
* **Beautiful UI:** Styled using the [Rich](https://github.com/Textualize/rich) library for elegant panels, colors, and markdown rendering.
* **Streaming Text:** Poems are typed out in real-time, simulating a digital typewriter.
* **Lightweight:** Optimized for quantized GGUF models (like TinyLlama), allowing it to run on standard laptops.

## 🛠️ Installation

### 1. Clone the Repo
```bash
git clone [https://github.com/YOUR_USERNAME/silicon-muse.git](https://github.com/YOUR_USERNAME/silicon-muse.git)
cd silicon-muse

```

### 2. Install Requirements

You need Python installed. Then run:

```bash
pip install rich llama-cpp-python

```

### 3. Download the Model (Crucial!)

This project requires a `.gguf` model file to work.

* **Download Link:** [TinyLlama-1.1B-Chat (Quantized)](https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v1.0-GGUF/blob/main/tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf) (~638 MB)

**Important:** Download the file `tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf` and place it in the same folder as the python scripts.

---

## 🎮 Usage

### Run the Standard poem generator

```bash
python main.py

```

*Enter a topic (e.g., "Cyberpunk City", "Lost Love", "The Ocean") and watch the poem generate.*

### Run the 3-word poem code

```bash
python muse.py

```

*Enter three words separated by spaces (e.g., `velvet thunder clock`) to see how the AI connects them.*

## ⚙️ Configuration

You can tweak the aesthetics or behavior by editing the constants at the top of the scripts:

```python
# Change colors
STYLE_BORDER = "cyan"
STYLE_PROMPT = "bold green"

# Change creativity (0.1 = boring, 0.9 = chaotic)
temperature = 0.8 

```

## 🤝 Credits

* **UI:** Built with [Rich](https://github.com/Textualize/rich).
* **Inference:** Powered by [llama-cpp-python](https://github.com/abetlen/llama-cpp-python).
* **Model:** [TinyLlama](https://github.com/jzhang38/TinyLlama) by TheBloke (GGUF quantization).

---

*Created with code and poetry.*
