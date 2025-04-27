
# Synthetic Medical Discharge Summary Generation (Gemini 2.5)

This project generates realistic synthetic hospital discharge summaries using Google's **Gemini 2.5 Flash Preview** model. It includes exploratory data analysis, synthetic data generation, and basic evaluation based on semantic similarity.

##  Project Structure

```
.
├── constants.py                # Stores your Gemini API key
├── eda.ipynb                 # Exploratory Data Analysis
├── generate_synthetic.ipynb # Generates synthetic summaries using Gemini
├── evaluation.ipynb         # Evaluates generated summaries (TF-IDF, token length, etc.)
├── results/                   # Contains generated and processed datasets
└── res/                  # Contains original examples used for prompting
```

## Features

### 1. Exploratory Data Analysis (`eda.ipynb`)
- Loads and analyzes the base dataset (`patient_data.json`)
- Computes token length distributions of real examples
- Visualizes diagnosis code distributions
- Prepares the base input for generation

### 2. Synthetic Summary Generation (`generate_synthetic.ipynb`)
- Uses the **Gemini 2.5 Flash Preview (04-17)** model
- Takes one primary ICD-10 code and 1–3 secondary codes as input
- Prompts are built to enforce:
  - Medical realism
  - Structural consistency
  - Anonymity (no names or identifiers)
- Generates 100+ synthetic patient summaries

### 3. Evaluation (`evaluation.ipynb`)
- Measures **TF-IDF cosine similarity** between summaries to check for redundancy
- Visualizes:
  - Cosine similarity matrix (heatmap)
  - Similarity score distribution
  - Token count distribution
- Provides simple statistical summaries (min, max, mean similarity)

## Requirements

- Python 3.8+
- Install dependencies via pip:

```bash
pip install pandas matplotlib seaborn scikit-learn tiktoken google-generativeai
```

- You also need a valid **Gemini API Key**. Set it in `constants.py` like this:

```python
API_KEY = "your-api-key-here"
```

## Improvements & Future Work

While the project demonstrates functional synthetic generation, several improvements could enhance the realism and quality of the dataset:

### Medical Coherence Checks
Add automatic validation of the medical logic between the diagnoses and the discharge text using Gemini or another LLM.

### Structural Consistency Checks
Review and refine the structure of the generated summaries to ensure they align with real-world formats (e.g., sections like “Chief Complaint,” “Hospital Course”).

###  Scoring System
Introduce a confidence or quality score to rank or filter synthetic examples.

### Human-in-the-Loop
Involve medical professionals to review a small portion of synthetic data to validate accuracy and realism.

## 👤 Author

Created by [Aurélien Ferlay](https://github.com/your-github-url) as part of the **SwissCoding** project.
