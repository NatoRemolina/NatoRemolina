<h1 align="center">Hi, I'm Natalia Remolina 👋</h1>
<h3 align="center">AI & Data Engineer · Production AI agents, RAG and data pipelines</h3>
<p align="center">Lambda Analytics · Engineering Physics at Universidad Nacional de Colombia · Medellín</p>

<p align="center">
  <a href="https://www.linkedin.com/in/natalia-patricia-remolina-rodriguez-1327a8220/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="mailto:nremolina@unal.edu.co"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
</p>

---

## ⚡ At a glance

- 🤖 **4 AI agents in production for 4 clients**: 1,000+ messages and ~100 voice calls a month (Lambda Analytics).
- 🎯 **84/95 vs. 69/95**: intent accuracy of my classifier vs. the previous rules, at **262 ms** median latency, validated in shadow mode.
- 🥉 **3rd place nationally**: Samsung Innovation Campus 2026 hackathon (RetailMind).
- 🏅 **Outstanding Performance Award**: Samsung Innovation Campus 2026.
- 🟢 **NVIDIA DLI**: Applications of AI for Anomaly Detection (Oct 2026).

---

## 👩‍🔬 About me

I build AI systems that reach production and stay there. My core work is conversational and voice
agents: I gather requirements with the client, design the knowledge base and the guardrails, ship
with FastAPI, LangGraph and Docker, and measure quality with MLflow and LangSmith. On the data side
I work with PySpark and SQL on Databricks and Delta Lake.

Before engineering, I was a Product Owner and a field data analyst, and I hold a technologist degree
in Project Management. That background is why I start from the business problem, not from the model.
I also research machine learning and quantum computing with the **QUANTA** and **SIMG** groups at
UNAL, and I'm a student volunteer at **IEEE Quantum Week 2026**.

---

## 💼 Experience

**AI & Data Engineer · [Lambda Analytics](https://github.com/LambdaAnalyticsSAS)** · Jan 2026 - present
- Built and maintain 4 production agents (WhatsApp, Twilio, voice with ElevenLabs) for 4 clients.
- Led the architecture of a property inventory agent, now in pilot with a real estate client (~40 inventories a month). See the case study below.
- Knowledge pipelines into ChromaDB with hybrid indexing and incremental updates; batch pipelines with PySpark on Databricks and Delta Lake; models served on Vertex AI; Docker deploys on AWS and GCP.

**Analyst / Product Owner · AIMEDIC** · Nov 2024 - Nov 2025
- Turned business needs into a prioritized backlog under Scrum; built 10 Power BI and Tableau dashboards used by senior management.

**Field Surveyor & Data Analyst · Municipality of Yopal** · 2017 - 2021
- Collected and validated SISBEN and OSIGD survey data; regression analysis for territorial projects.

---

## 🏗️ Case study: property inventory agent (client work, code is private)

A Telegram agent that guides a real estate agent through a property visit and builds the inventory
record (PostgreSQL + PDF) from text, audio, photos and video. The key design decision: **no model
writes to the record directly**. Every action goes through a harness written in code.

```mermaid
flowchart LR
    U[Agent on Telegram<br/>text, audio, photos, video] --> P[Perception<br/>Gemini + YOLO on photos]
    P --> J[Jev<br/>lightweight intent classifier]
    J -. rare cases .-> L[gpt-5.5 fallback]
    J --> H[Harness<br/>function registry, preconditions,<br/>single-use approvals, invariants]
    L --> H
    H --> D[(PostgreSQL)]
    D --> R[Inventory PDF]
```

- Every change runs first in **shadow mode** with non-regression tests.
- On 95 new phrases, Jev got **84 right vs. 69** for the previous rules, with **no false "yes"**, **262 ms** median latency and an estimated **~US$0.0035 per inventory**.
- I led the architecture, the WhatsApp-to-Telegram migration and the phased roadmap.

---

## 📂 Featured projects

| Project | What it does | Result | Stack |
|---------|--------------|--------|-------|
| **[VALAI: post-op voice agent](https://github.com/NatoRemolina/postop-voice-agent)** | Spanish voice agent that calls post-surgery patients, grounds every clinical answer in real guidelines with source and page citations, and escalates to a human. Tech Sphere Challenge 2026. | MVP deployed on AWS · **~1 s** median time to first token (P50 992 ms) | `FastAPI` `LangGraph` `Hybrid RAG` `ElevenLabs` `MLflow` |
| **[RetailMind](https://github.com/NatoRemolina/Dataholics-Samsung-Innovation-Campus-2026)** | Weekly sales and inventory forecasting for 85 customers over 156 weeks (~9M units), with leakage-free features and an [interactive dashboard](https://giovacode1.github.io/Dataholics). My part: data cleaning and model training. | **3rd place nationally** · sales MAE 12.94 → **11.76**, R² 0.06 → **0.47** | `Python` `pandas` `scikit-learn` `Power BI` |
| **[Credit Risk](https://github.com/Team5RNABI/credit-risk-ml-nn)** | Interpretable scorecard vs. a neural network for probability of default, with Optuna, early stopping and imbalanced-class metrics. | Scorecard won on test: **ROC-AUC 0.79** | `PyTorch` `scikit-learn` `Optuna` |
| **[Educational Analytics](https://github.com/Capstone-Tech-Tailors/Analitica-Educativa)** | Teacher SWOT analyses from a fine-tuned sentiment model, plus dropout and turnover models. Universidad del Rosario capstone. | Deployed on Azure Container Apps | `FastAPI` `NLP` `Azure` `Power BI` |
| **[EPM Conversational Agent](https://github.com/NatoRemolina/Agente-Conversacional-EPM)** | RAG assistant that checks water-service outages in Medellín via web scraping and answers with citations to official documents. | | `LangChain` `FAISS` `Selenium` `FastAPI` |
| **[Tourism Recommender](https://github.com/Team5RNABI/timeseries-vision-recommender-)** | Hybrid destination recommender with a demand-forecasting module. | | `Prophet` `scikit-learn` |

### More projects

- **[Real-Time Object Detection](https://github.com/NatoRemolina/roboflow-detector)**: PWA that runs COCO computer-vision inference from a phone camera, no install. `JavaScript` `Vercel` `Roboflow`
- **[MeIA 2025, Sargassum Prediction](https://www.kaggle.com/competitions/meia-2025-sargazo-prediction/overview)**: CNN image classification (ResNet, VGG) of sargassum levels on Caribbean beaches. Kaggle.
- **Sentiment Analysis of Economic News**: 7,125 Spanish financial texts, TF-IDF + logistic regression, macro-F1 up to 0.70. Course repo, private until the program ends.

---

## 🛠️ Tech stack

**AI & agents**

![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat&logo=langchain&logoColor=white)
![LangSmith](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat&logo=langchain&logoColor=white)
![RAG](https://img.shields.io/badge/Hybrid%20RAG-10A37F?style=flat)
![ChromaDB](https://img.shields.io/badge/ChromaDB-FF6446?style=flat)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat&logo=googlegemini&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white)
![ElevenLabs](https://img.shields.io/badge/ElevenLabs-000000?style=flat&logo=elevenlabs&logoColor=white)

**Machine learning & MLOps**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat&logo=mlflow&logoColor=white)
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat&logo=apacheairflow&logoColor=white)
![YOLO](https://img.shields.io/badge/YOLO-111F68?style=flat)

**Data**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat&logo=databricks&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD4?style=flat)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat&logo=googlebigquery&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)

**Backend, cloud & automation**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat)
![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat&logo=googlecloud&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat&logo=n8n&logoColor=white)
![Twilio](https://img.shields.io/badge/Twilio-F22F46?style=flat&logo=twilio&logoColor=white)
![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=flat&logo=whatsapp&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=flat&logo=telegram&logoColor=white)

**BI**

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat)

---

## 📚 Currently learning (until Dec 2026)

- **Advanced Machine Learning & Data Science Diploma** · Universidad Nacional de Colombia (192 h: NLP, deep learning, agile ML).
- **Machine Learning Diploma** · Universidad de Antioquia (90 h: deep neural networks, CNNs, RNNs).
- **GCI World 2026, Data Science Program** · Matsuo-Iwasawa Lab, The University of Tokyo.
- **[Object-Oriented Programming](https://github.com/NatoRemolina/UNAL-Programacion-Orientada-a-Objetos)** · Universidad Nacional de Colombia.

---

## 🏆 Achievements

- 🥉 **3rd place nationally**, Samsung Innovation Campus 2026 hackathon (team Dataholics).
- 🏅 **Outstanding Performance Award**, Samsung Innovation Campus 2026 (Samsung Electronics Colombia & Universidad del Rosario).
- 🟢 **NVIDIA Deep Learning Institute**, Certificate of Competency: Applications of AI for Anomaly Detection (2026).
- 🌐 **Student Volunteer**, IEEE Quantum Week 2026 (QCE26), Toronto.
- 🎓 **[Scholarship, 8th Colombian HPC Summer School](https://www.cybercolombia.org/summer_school_8/#cybercolombia-scholarship-awardeesrtir)** (CyberColombia).
- 🎓 **Scholarship**, Introduction to Quantum Computing (The Coding School / Google Quantum AI).
- 🎓 **Scholarship**, Advanced Data Analysis Diploma (Talento Tech, MinTIC / UdeA).
- 🚀 **Georgia Tech CREATE-X**, Medellín Cohort 3 (2024).
- 🧠 **MeIA 2025**, AI macro-training (UNAM).

---

## 🎯 What I'm looking for

> **AI Engineer, ML Engineer (MLOps) or Data Engineer** roles in teams that build, scale and improve AI systems in production.

<p align="center">
  <a href="https://www.linkedin.com/in/natalia-patricia-remolina-rodriguez-1327a8220/">LinkedIn</a> ·
  <a href="mailto:nremolina@unal.edu.co">nremolina@unal.edu.co</a>
</p>
