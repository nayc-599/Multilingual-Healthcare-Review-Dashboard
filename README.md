# Multillingual Healthcare Review Dashboard

![Status](https://img.shields.io/badge/Status-Complete-success)
![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Project Description
An end-to-end NLP pipeline designed to make Russian-language patient healthcare reviews accessible to English-speaking researchers, analysts and policymakers – without requiring Russian language expertise from the end user.

**Live Demo:** [Try it here!](https://public.tableau.com/app/profile/nay.c4691/viz/RussianHealthcareReviewsDashboard/Dashboard1)

## Purpose
Understanding patient experiences is critical for improving healthcare quality, yet sourcing a suitable dataset for this kind of analysis is a common challenge. No English-language dataset of healthcare facility reviews was available that met the requirements of this project. A Russian-language dataset was identified as the closest suitable alternative, making translation a necessary first step rather than an optional one.
This project addresses that constraint by:

- Translating Russian healthcare facility reviews into English, making the data usable for English-speaking analysis
- Extracting the top 10 topics to identify the dominant themes and key pain points
- Summarising representative reviews to provide human-readable snapshots of real patient sentiment

## Features
- **Preprocessing:** Cleaning, tokenisation and lemmatisation of Russian reviews using nltk for stopwords removal and Natasha for lemmatisation.
- **Topic Modeling:** Benchmarked BERTopic against LDA, optimising LDA as best model with 20% Coherence Score baseline improvement.
- **Translation Pipeline:** Translated top 10 topic representative Russian reviews to English using Helsinki-NLP model.
- **Review Summarisation:** Summarised translated reviews using distilbart.
- **Keyword Extraction:** Top 5 most meaningful terms manually curated with the aid of ChatGPT, as automated methods (TF-IDF and KeyBERT) did not produce sufficiently meaningful results.

## Tech Stack
- **Python/Pandas**: Data wrangling and feature engineering
- **Jupyter Notebook**: Development and analysis
- **HuggingFace Transformers**: Translation and summarisation models
- **Tableau**: Dashboard visualisation
- **Git & GitHub**: Version control

## Prerequisites
- Python 3.8 or higher
- pip package manager

## Installation
1. Clone the repository:

    ``` bash
   git clone https://github.com/nayc-599/Multilingual-Healthcare-Review-Dashboard.git
    ```
  
    ```bash
   cd Multilingual-Healthcare-Review-Fashboard
    ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```
   
3. Open the notebooks:
   
   ```bash
   jupyter notebook
   ```

4. Run the notebooks in order.

## Dataset
**Size:** 10,000 Sample Russian Reviews from 70,000 Original Russian Reviews

**Review Content**
- Source: Russian-language healthcare facility reviews
- Language: Russian (translated to English as part of the pipeline)
- Domain: Patient experience — covering doctors, facilities, wait times, treatment, and staff

**Why Russian?**
No suitable English-language dataset of healthcare facility reviews was available for this project. The Russian dataset was chosen as the best available alternative, with translation built into the pipeline to bridge the language gap.

## Project Structure
 ```
    ├── data
    │   └── raw
    │       └── healthcare_facilities_reviews.jsonl.gz
    │   └── sample
    │       └── sample_processed_reviews.csv
    │   └── summary
    │       └── summaries.csv
    │   └── healthcare_facilities_reviews_embeddings.npy
    ├── screenshots
    │   └──image.png
    ├── notebooks
    │   ├── 01_preprocessing.ipynb
    │   ├── 02_model_training.ipynb
    │   └── 03_analysis.ipynb
    ├── .gitignore
    ├── README.md
    └── requirements.txt
 ```

## Results
### Top 10 Topics
1. Pediatric Care
2. Medical Teams
3. Dental Clinic Services
4. Administration
5. ICU & Emergency Care
6. Maternity Care
7. Neurosurgery
8. Dental Procedures
9. Optical Services
10. Other

### Representative Review Summary
` A friend of ours died yesterday in ICU, and he was transferred from another hospital to a neuroanimation . The department doesn't pick up the phone, and the reception room won't help, he writes . "There's no way to know the state of the patient," he says . "What's going on outside the resuscitation room, it's impossible to know and understand, isolation is worse than in prison" `
