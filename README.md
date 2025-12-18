# Clustering_explanations
Attention mechanisms for explaining time-series clustering

📌 Models Overview
1️⃣ LSTM (Baseline)

A standard LSTM classifier that processes variable-length time-series to predict the number of clusters where each individual belongs (clustering-independent output)

Output: class logits

2️⃣ LSTM + Temporal Attention

An LSTM followed by an additive attention mechanism over time steps:

Input → LSTM → Temporal Attention → Classifier


This allows the model to focus on the most informative time steps and improve interpretability via attention weights

Outputs: class logits

3️⃣ Feature + Temporal Attention (Multi-Head Attention)

A dual-attention model that applies:

- Feature attention (across variables)

- Temporal attention (across time steps)

Input
 ├─ Feature Attention
 ├─ Temporal Attention
 └─ Concatenation → Classifier


Outputs: class logits, feature attention weights, temporal attention weights

🗂 Repository Structure
.
├── models/
│   ├── LSTM.py
│   ├── LSTM_att.py
│   ├── LSTM_att_training.py
│   ├── FeatTempAttClassifier.py
│   └── FeatTempAttClassifier_training.py
│   └── TempAtt_vizualization.py
│   └── FeatTempAtt_vizualization.py
├── requirements.txt
└── README.md

📥 Input Format

All models expect input tensors of shape:

(batch_size, time_steps, num_features)


