# NER Evaluation Using LLMs for Real Estate Chat Conversations

This repository contains my submission for the **AI Research Intern – Screening Assignment**, focused on evaluating large language models (LLMs) for named entity extraction (NER) from unstructured real estate chat conversations.

---

##  Objective

The goal of this project is to:
- Extract structured entities from informal chat conversations
- Evaluate multiple LLMs and prompt strategies under strict non-inference rules
- Compare models using quantitative metrics (Precision, Recall, F1)
- Analyze trade-offs across accuracy, latency, token usage, and reliability

---

## 📂 Project Structure
├── notebooks/  
│ ├── 01_run_models.ipynb # Model execution & output generation  
│ └── 02_evaluation.ipynb # Parsing, metrics, and analysis  
├── data/  
│ └── gold_labels.json # Manually created ground-truth labels  
├── outputs/  
│ ├── *_raw.json # Raw model outputs  
│ └── *_metrics.json # Latency & token usage metrics  
├── requirements.txt # Python dependencies (pinned versions)  
├── .env.example # Environment variable template  
└── README.md  


---

## 🧠 Models Evaluated

- **GPT-OSS (120B)** – Strong instruction-following and structured JSON reliability  
- **LLaMA (llama-3.3-70b)** – Efficient open-weight model with low latency  
- **Qwen (qwen3-32b)** – Open-source model used to evaluate prompt sensitivity  

All models were evaluated using API-based inference to ensure stability and fair comparison.

---

## 📝 Prompt Strategies

Six prompt strategies were tested:
1. Naive baseline  
2. Schema-strict prompt  
3. Hidden reasoning prompt  
4. Negative instruction prompt  
5. One-shot prompt  
6. **Entity-by-Entity prompt (best-performing)**  

Prompt Strategy 6 consistently achieved the highest F1 scores across all models.

---

## 📊 Evaluation Methodology

- **Gold labels** were manually created without LLM assistance
- Exact-match comparison at the entity level
- Metrics used: **Precision, Recall, Micro-averaged F1**
- Invalid or malformed JSON outputs were treated as failures
- No inference or hallucination was permitted

---

## ⏱️ Latency & Token Usage (Summary)

| Model    | Avg Latency (s) | Prompt Tokens | Total Tokens |
|---------|----------------|---------------|--------------|
| GPT-OSS | ~3.01          | 400–600       | 730–1140     |
| LLaMA   | ~1.8           | 400–600       | 475–720      |
| Qwen    | ~5.5           | 400–600       | 700–1600     |

---

## 🏆 Final Recommendation

**GPT-OSS with Entity-by-Entity Prompting** achieved the best balance of precision, recall, reliability, and structured output consistency, resulting in the highest overall F1 score.

---

## 🔁 Reproducibility

1. Clone the repository  
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
  
3. Create a .env file using .env.example

4. Run notebooks in order:
- 01_run_models.ipynb
- 02_evaluation.ipynb

## Notes
No API keys are included in this repository

All outputs are generated programmatically

This repository is shared solely for evaluation purposes
