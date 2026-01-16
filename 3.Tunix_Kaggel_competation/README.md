# GRPO Training on ARC Science Questions with Gemma 2

This repository demonstrates how to fine-tune the **Gemma 2 2B-IT** model to solve grade-school science questions using **Group Relative Policy Optimization (GRPO)**.

The project uses the [AI2 Reasoning Challenge (ARC)](https://allenai.org/data/arc) dataset and trains the model to "think" before answering by enforcing a structured reasoning format.

## Team Information

**Team Name:** [THWS PHY]

**Members:**
- [Yashaswini Suresh]
- [Yashwanth Goud Chithaloori] 
- [Harshith Babu Prakash Babu] 
- [Prahas Hegde]

## Why We Chose the ARC Dataset

The Google Tunix Hackathon reference notebook used the **GSM8K math dataset**. However, the hackathon guidelines specifically asked participants to explore **non-math domains** to demonstrate the versatility of GRPO.

We chose the **ARC (AI2 Reasoning Challenge) Science Dataset** because:

1. **Non-Math Domain:** ARC contains science questions covering physics, biology, chemistry, and earth science—completely different from the reference math problems.
2. **Structured Reasoning Required:** Science questions require analyzing multiple options and applying scientific knowledge, making it ideal for training reasoning traces.
3. **Clear Evaluation:** Multiple-choice format (A, B, C, D) allows objective accuracy measurement.
4. **Public Availability:** The dataset is freely available, ensuring reproducibility.


## Results

By applying GRPO with custom reward functions, the model achieved significant improvements over the random baseline:

| Metric | Result | Baseline (Random) |
| :--- | :--- | :--- |
| **Answer Accuracy** | **55.0%** | 25.0% |
| **Format Compliance**| **80.0%** | ~0% |

## Key Features

* **Model:** Gemma 2 2B-IT (Instruction Tuned)
* **Method:** Group Relative Policy Optimization (GRPO)
* **Technique:** Low-Rank Adaptation (LoRA) for efficient fine-tuning (Rank=64)
* **Framework:** JAX, Flax NNX, and Tunix
* **Hardware:** Optimized for TPU v5e

## Methodology

### The GRPO Approach
Unlike standard Supervised Fine-Tuning (SFT), this project uses Reinforcement Learning. The model generates a group of outputs for every question, and the best outputs are reinforced based on a set of reward functions.

### Reward Functions
We utilized four specific reward functions to guide the model's behavior:
1. **`match_format_exactly`**: Rewards the model for strictly following the XML tag structure.
2. **`match_format_approximately`**: Partial credit for getting close to the correct format.
3. **`check_reasoning_quality`**: Rewards the presence of step-by-step analysis (e.g., using words like "therefore", "because", "Option A").
4. **`check_answer_correct`**: A high-value reward for selecting the correct multiple-choice option (A, B, C, or D).

### Output Format
The model is trained to output its reasoning before the final answer:
```xml
<reasoning>
Let me analyze the options...
- Option A is incorrect because...
- Option B fits the description because...
</reasoning>
<answer>B</answer>
```

## Repository Contents

* `Gemma2_ARC_dataset.ipynb` - Main training notebook
* `README.md` - This file

## Hackathon Submission

This project was created for the **Google Tunix Hackathon** on Kaggle.

**Notebook Link:** [GRPO Demo - New Data](https://www.kaggle.com/code/yashaswinikushi/gemma2-arc-dataset)
**Write up Link:** [Hackathon submission](https://www.kaggle.com/competitions/google-tunix-hackathon/writeups/teaching-gemma-to-think-first-reasoning-traces-on)
**Youtube Link:**(https://www.youtube.com/watch?v=eRcqrxqR1Lo&t=1s)

## References

* [Tunix Library](https://github.com/google/tunix)
* [ARC Dataset](https://allenai.org/data/arc)
* [GRPO Paper](https://arxiv.org/pdf/2402.03300)
* [Gemma 2 Model](https://deepmind.google/models/gemma/)




