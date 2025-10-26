# Model-compression-sustainability-analysis
Comparative study on the environmental impact of model compression techniques — Quantization, Pruning, and Knowledge Distillation — applied to DeepSeek-Coder 1.3B using the CodeCarbon framework. 
# 🧠 Model Compression and Green AI  
### *Comparative Environmental Impact of Model Compression Techniques*  
*Author: Dhruvi Rajeshkumar Thakkar*  
*Course: AI for Sustainable Computing — University of Calgary*

---

## 📘 Overview  
This repository presents **Assignment 2**, which explores the environmental efficiency of three model-compression techniques — **Quantization**, **Structured Pruning**, and **Knowledge Distillation** — applied to the `DeepSeek-Coder-1.3B` transformer model.  

The study uses the **CodeCarbon** framework to measure energy usage and CO₂ emissions during inference.  
The objective is to analyze the trade-off between **sustainability (energy/emission savings)** and **model performance**.

---

## ⚙️ Methods  
Each model was tested using the same benchmark task — **Python docstring generation** — to ensure consistent computational load.  

| Compression Method | Description |
|:--|:--|
| **Baseline (FP32)** | Uncompressed DeepSeek-Coder 1.3B model in full precision. |
| **Quantized (8-bit)** | Model weights reduced to 8-bit precision using BitsAndBytes. |
| **Structured Pruned (20%)** | 20 % of Linear layer weights removed via L2-norm structured pruning. |
| **Distilled (Tiny GPT-2)** | Lightweight student model trained to mimic the DeepSeek teacher. |

Each configuration was executed for 3–5 epochs using CodeCarbon’s emission tracker.

---

## 📊 Results Summary  

| Model | Compression | Size (MB) | CO₂ (kg eq) | Energy (kWh) | Latency (s) | Accuracy (P/F) |
|:--|:--|:--:|:--:|:--:|:--:|:--:|
| Baseline | FP32 | 1300 | 0.00150 | 0.00040 | 14.2 | F |
| Quantized | 8-bit | 350 | 0.00110 | 0.00031 | 9.8 | F |
| Pruned | 20 % Structured | 600 | 0.00120 | 0.00033 | 10.5 | F |
| Distilled | Tiny GPT-2 | **30** | **0.00065** | **0.00018** | **2.5** | F |

**Key Findings**
- Model size and CO₂ emissions are strongly inversely correlated (**r ≈ –0.91**).  
- Distillation achieves the **lowest emissions (0.00065 kg CO₂)** and **fastest latency (2.5 s)**.  
- Quantization is the most practical real-world method for quick emission savings.  
- All models failed the heuristic docstring accuracy check but successfully demonstrate environmental benefits.

---

## 🌱 Visualization  

**Figure 1 — CO₂ Emissions by Model**  
*Emission drops steadily with compression level.*

**Figure 2 — Latency by Model**  
*Distilled model performs 6× faster than baseline.*


---

## 🧮 Code Structure  

├── baseline_results.py
├── quantized_results.py
├── pruned_results.py
├── distilled_results.py
├── emissions_summary.csv
└── Assignment2_ModelCompression_SustainabilityReport.pdf
