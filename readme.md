# 🩺 Physician Notetaker – NLP Pipeline

## Overview
In this assignment I implemented an end-to-end **Physician Notetaker NLP Pipeline** system that processes doctor–patient conversations and produces structured medical documentation.

The solution focuses on:
- Medical entity extraction
- Structured medical summarization
- Patient sentiment and intent analysis
- SOAP note generation.

The implementation emphasizes **clarity, explainability, and healthcare-safe design**.

---

## Problem Statement
Given a transcribed physician–patient conversation, build an NLP pipeline that:
1. Extracts key medical details (Symptoms, Diagnosis, Treatment, Prognosis)
2. Analyzes patient sentiment and intent
3. Converts the conversation into a structured SOAP note format


---

## Tech Stack
- **Python**
- **Jupyter Notebook**
- **spaCy** – text processing and noun phrase extraction
- **HuggingFace Transformers**
  - Biomedical NER model
  - DistilBERT for sentiment analysis
- **Rule-based logic** for clinical safety and determinism

---

## Approach

### 1. Text Preprocessing
- Normalized the raw transcript by:
  - Removing formatting artifacts
  - Standardizing speaker labels (Doctor / Patient)
  - Ensuring one speaker per line
- This improves speaker segmentation and model reliability.

---

### 2. Medical NLP Summarization
- Used a **hybrid approach**:
  - Transformer-based Medical NER for entity extraction
  - Rule-based enrichment for diagnosis and prognosis
- Extracted:
  - Symptoms
  - Diagnosis
  - Treatment
  - Current status
  - Prognosis
- Generated a structured medical summary in **JSON format**.

---

### 3. Sentiment & Intent Analysis
- Performed sentiment analysis **only on patient utterances** to avoid contamination from physician reassurance.
- Used a pretrained **DistilBERT** model for sentiment classification.
- Applied rule-based logic for intent detection (e.g., reporting symptoms, seeking reassurance).

---

### 4. SOAP Note Generation (Bonus)
- Converted the transcript into a structured **SOAP note**:
  - **Subjective** – patient-reported symptoms and history
  - **Objective** – physician examination findings
  - **Assessment** – diagnosis and severity
  - **Plan** – treatment and follow-up
- Used deterministic rules to ensure clinical readability and explainability.

---

## Design Considerations
- **Hybrid NLP (ML + Rules):** Improves robustness and reduces hallucination risk.
- **Explainability:** Structured outputs and rules are preferred in healthcare settings.
- **No Model Training:** Pretrained models are used in inference mode to avoid unnecessary complexity.
- **Safety First:** Missing or ambiguous medical data is explicitly marked instead of inferred.

---

## How to Run
1. Install required dependencies:
   ```bash
   pip install spacy transformers torch
   python -m spacy download en_core_web_sm

2. Open the notebook:
   ```bash
    PhysicianNotetaker.ipynb

3. Run the cells sequentially from top to bottom.S

