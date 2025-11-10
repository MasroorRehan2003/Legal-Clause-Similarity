# 🧠 Legal Clause Similarity – Deep Learning Assignment 2 (CS-452)

This project focuses on detecting **semantic similarity between legal clauses** using deep learning models such as **BiLSTM** and **Attention-based neural networks**.  
It was completed as part of the **Deep Learning (CS-452)** course at **FAST NUCES**.

---

## 📂 Project Overview

Legal documents contain thousands of clauses with overlapping meanings but different wordings.  
The goal of this project is to determine whether **two clauses express the same legal intent** or not.

### 🧩 Key Objectives
- Build an NLP model that can measure **semantic similarity** between pairs of legal clauses.
- Compare different architectures such as **BiLSTM**, **Attention**, and a **Hybrid BiLSTM+Attention** model.
- Evaluate performance using multiple metrics: Accuracy, Precision, Recall, F1-score, and ROC-AUC.

---

## 📊 Dataset

- **Source:** [Legal Clause Dataset on Kaggle](https://www.kaggle.com/datasets/bahushruth/legalclausedataset)
- **Files:** 395 CSVs (≈150,000 clauses)
- **Columns:**  
  - `clause_text` – Text of each legal clause  
  - `clause_type` – Label identifying the clause category  
- Pairs were created randomly for similarity detection.

---

## ⚙️ Preprocessing Steps
- Lowercasing and punctuation removal  
- Stopword filtering  
- Tokenization with Keras `Tokenizer`  
- Padding sequences to uniform length  
- 80/20 split into training and test sets

---

## 🧱 Model Architectures

### 🟩 **1. BiLSTM Model**
A bidirectional LSTM network that captures contextual dependencies in both directions.

**Architecture:**

---

### 🟦 **2. Attention Model**
A basic encoder with Keras `Attention` layer to align relevant features between the two input sequences.

---

### 🟧 **3. BiLSTM + Attention Hybrid**
Combines the representational strength of BiLSTM with an Attention mechanism for feature weighting.

---

## 📈 Model Training Results

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|--------|-----------|------------|--------|-----------|-----------|
| **BiLSTM** | **0.9567** | 0.9281 | 0.9894 | **0.9578** | **0.9570** |
| **Attention** | 0.5397 | 0.5310 | 0.6127 | 0.5690 | 0.5404 |
| **BiLSTM + Attention** | 0.6060 | 0.6029 | 0.6011 | 0.6020 | 0.6060 |

📌 **Observation:**  
The BiLSTM model achieved the best overall performance due to its ability to capture long-term dependencies in textual sequences.

---

## 📉 Training Curves
The training and validation accuracy graphs show strong convergence for the BiLSTM model, with minimal overfitting.

---

## 🧠 Insights & Discussion
- Attention alone underperformed due to insufficient contextual depth.
- The BiLSTM+Attention hybrid improved slightly but did not surpass pure BiLSTM.
- Clause-level similarity detection benefits more from sequential modeling than from isolated attention mechanisms.

---

## 🧪 Evaluation Metrics
Implemented using `sklearn.metrics`:
- `accuracy_score`
- `precision_score`
- `recall_score`
- `f1_score`
- `roc_auc_score`

---

## 💡 Sample Results

| Clause 1 | Clause 2 | Prediction |
|-----------|-----------|------------|
| "This Agreement shall be governed by applicable law." | "The governing law for this Agreement shall be applicable law." | ✅ Similar |
| "Waivers may be granted by the Company with written consent." | "The Servicer shall have no right to grant waivers." | ❌ Not Similar |

---

## 🧰 Requirements

```bash
numpy
pandas
tensorflow
keras
scikit-learn
matplotlib
