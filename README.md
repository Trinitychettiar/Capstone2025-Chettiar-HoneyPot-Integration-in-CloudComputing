

# ☁️ HoneyCloud – Honeypot Integration in Cloud Computing for Threat Intelligence.

![Python](https://img.shields.io/badge/Python-3.9-blue)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

This repository contains the complete codebase, documentation, and experimental outputs for the capstone project titled **HoneyCloud**, which explores the deployment of **honeypots in cloud environments (AWS, GCP, Azure)** and the use of **deep learning models** to identify, classify, and detect cyber threats using real-world attack data.

The project combines **honeypot-based threat collection** with **supervised and unsupervised machine learning**, including anomaly detection via autoencoders, classification via MLPs, and dashboard-based operational monitoring via **Elastic Stack (ELK)**.

---

## 📚 Table of Contents

- [🔍 Project Overview](#project-overview)
- [📦 Dataset](#dataset)
- [🛠️ Methodology](#methodology)
- [📊 Experiments & Results](#experiments--results)
- [🧠 Explainability and Insights](#explainability-and-insights)
- [📈 Dashboard and Real-Time Logs](#dashboard-and-real-time-logs)
- [🚧 Limitations and Future Work](#limitations-and-future-work)
- [👥 Contributors](#contributors)
- [📄 License](#license)
- [🙏 Acknowledgments](#acknowledgments)

---

## 🔍 Project Overview

With cloud platforms becoming central to enterprise infrastructure, the frequency and sophistication of attacks targeting cloud services has increased. This project focuses on simulating vulnerable services using **honeypots** and collecting attack logs. The collected data is analyzed using **machine learning** models to classify known attacks and detect unknown or novel anomalies.

Honeypots used include: Cowrie, Dionaea, Glastopf, Heralding, and more. These were deployed across **AWS** and **Azure** using **T-Pot framework** and containerized services. **GCP** will be used in further updates.

---

## 📦 Dataset

- **Sources**: Logs collected from real honeypots deployed in the cloud.
- **Fields**: `cloud_provider`, `honeypot_type`, `source_ip`, `asn`, `region`, `protocol`, `port`, `bytes_in/out`, `event_type`, `cve_id`, `reputation_score`, etc.
- **Format**: CSV files structured and normalized for ML tasks.
- **Duration**: Logs collected over a 4-week period (5th July – 2nd August).

---

## 🛠️ Methodology

1. **Deployment of Honeypots** across AWS, Azure, and GCP using T-Pot.
2. **Data Collection** and conversion into structured CSV format.
3. **Data Preprocessing**:
   - One-hot encoding of categorical features
   - Z-score normalization of numeric fields
4. **Supervised Learning (MLP)**:
   - Attack classification using PyTorch MLP
   - Hyperparameter tuning and evaluation
5. **Unsupervised Learning (Autoencoder)**:
   - Anomaly detection using reconstruction error
   - Scores standardized using Z-score and percentile ranks
6. **Risk Scoring**:
   - Combining classifier confidence + anomaly percentile + CVE severity
7. **Elastic Stack Integration**:
   - Kibana dashboards for live threat visualization

---

## 📊 Experiments & Results

- **Supervised Learning**:
  - MLP Accuracy: ~86%
  - Macro F1-score: 0.76
  - 20 attack classes including brute-force, exploit attempts, malware delivery

- **Unsupervised Learning**:
  - Autoencoder flagged rare/unknown attacks
  - Identified top 20 anomalies with high deviation scores

- **Visual Outputs**:
  - Confusion matrix
  - SHAP summary plots
  - Anomaly score histograms
  - Kibana dashboards

---

## 🧠 Explainability and Insights

- **SHAP Analysis** was used to understand model decision-making:
  - Top features impacting predictions: `reputation_score`, `honeypot_type`, `source_country`
  - Helps validate model trustworthiness and ensure fairness

- **ELI5** used for simple local explanations to interpret why a specific prediction was made.

---

## 📈 Dashboard and Real-Time Logs

Elastic Stack integration enables:
- Real-time monitoring of attacks
- Visuals for top IPs, ports, honeypots, and attack types
- Severity-based filtering using custom risk scores
- Maps showing geo-distribution of attackers

<img src="images/kibana_dashboard.png" width="700"/>

---

## 🚧 Limitations and Future Work

- **Limitations**:
  - Evasion possible by advanced attackers detecting honeypots
  - High resource consumption by high-interaction honeypots
  - Legal/ethical considerations in public cloud environments

- **Future Enhancements**:
  - Use **Reinforcement Learning** for real-time defense decisions
  - Deploy **AI-based adaptive honeypots**
  - Integrate with threat feeds and SIEM tools for enterprise use

---

## 👥 Contributors

- Trinity Chettiar – MSc Cybersecurity | Cloud & AI Enthusiast  
- Special thanks to my guide, faculty, and lab mentors for continuous feedback and evaluation support.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙏 Acknowledgments

- T-Pot Honeypot Framework (Deutsche Telekom Security)
- Elastic Team for the ELK Stack
- PyTorch & Scikit-Learn for model training
- GitHub Copilot and ChatGPT for AI-assisted development
- University Capstone Lab (Cybersecurity Department)

---

🛡️ *“Cybersecurity is not just about protecting systems, it’s about predicting the attacker’s next move. Honeypots give us the lens into that future.”*
