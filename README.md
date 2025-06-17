# 🕵️‍♂️ Mapping Illicit Flows: A Machine Learning Approach to Anti-Money Laundering (SUS8 Hackathon)

## 🏆 Awarded:
**🥇 1st Place & Best Project Overall**  
*Stats Under the Stars 8 Hackathon* (#SUS8)  
Organized by [Società Italiana di Statistica](https://sis2025.sis-statistica.it/) & [Rulex](https://www.rulex.ai)

---

## 📌 Overview

This project was developed as part of the SUS8 2025 hackathon challenge on **Anti-Money Laundering (AML)**. The goal was to build a high-performing machine learning pipeline to detect **suspicious money laundering transactions** within a largely legitimate transaction dataset — a typical scenario in real-world financial systems.

We designed a graph-based, cost-sensitive ensemble architecture using **XGBoost** and **LightGBM**, enriched with **topological features** extracted from transaction networks.

---

## 🧠 Problem Statement

Financial institutions must detect and prevent **money laundering**, a process that hides illicit funds within legitimate transactions. This problem is particularly difficult due to:

- Rarity of fraudulent activities (extreme class imbalance)
- Sophisticated mimicking of normal transaction behavior
- Lack of immediate fraud labels (delayed supervision)

**Provided Dataset**: Simulated banking transactions, with a very small subset labeled as suspicious.

**Objective**:  
Train a binary classifier to flag laundering transactions as accurately and robustly as possible.

---

## 📊 Evaluation Metrics

A custom composite score was used, reflecting real-world AML priorities:

1. **AUC** – Ability to distinguish fraudulent vs. non-fraudulent
2. **Balanced Accuracy** – Accounts for class imbalance
3. **Fraud Capture Rate (Top 485)** – % of frauds captured in the top-485 most suspicious predictions

> 🧮 Final score = Arithmetic Mean of AUC, Balanced Accuracy, and Fraud Capture Rate

---

## 🚀 Our Approach

### 1. 🕸️ Graph-Based Feature Engineering
We modeled the transaction dataset as a **directed graph**:
- **Nodes** = accounts
- **Edges** = money transfers

Extracted topological features:
- `in/out degree` centrality
- `betweenness centrality` (intermediary detection)
- `pair frequency` and `is_circular` flags
- `multi-account patterns` and peer-repetition scores

### 2. 📦 Machine Learning Pipeline
- Models: **XGBoost** & **LightGBM**
- Optimization: **Optuna** with TPE sampler
- Strategy: **Cost-sensitive learning** to address class imbalance
- Cross-validation: **5-fold stratified**

### 3. 🤝 Model Ensembling
We combined model outputs using a weighted ensemble:
```
P_final = 0.4 * P_LGBM + 0.6 * P_XGBoost
```
This allowed us to blend LightGBM's deep local patterns with XGBoost's strong regularization and stability.

---

## ✅ Results

| Metric               | Private Leaderboard | Final Leaderboard |
| **Final Score**      | **0.72054**         | **0.76869**        |

> The significant **increase from private to final leaderboard** confirmed our model's **robustness and generalization**, mitigating overfitting effectively.

---

## 📎 Resources

- 📄 [Competition Website](https://www.datachallenge.it/competitions/257)  
- 🌐 [SUS 2025 Info](https://sites.google.com/view/sus2025-statsunderthestars/)

---

## 👥 Team

- [Giuseppina Iannotti](https://www.linkedin.com/in/giuseppina-iannotti-22331535a/)
- [Alessia Migneco](https://www.linkedin.com/in/alessia-migneco-7a3932231/)
- [Sara Pantini](https://www.linkedin.com/in/sara-pantini-4401b6270/)
- [Emanuele Iaccarino](https://www.linkedin.com/in/emanuele-iaccarino-a4298b27b/)

---

## 📬 Contact

For any questions, feel free to open an issue or reach out via LinkedIn!

---

## 📝 License

This project is licensed under the MIT License.
