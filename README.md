# Multilingual Healthcare Review Dashboard

![Status](https://img.shields.io/badge/Status-Complete-success)
![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Project Overview
An end-to-end NLP pipeline designed to make Russian-language patient healthcare reviews accessible to English-speaking researchers, analysts and policymakers – without requiring Russian language expertise from the end user.

**Live Dashboard:** [Try it here!](https://public.tableau.com/views/RussianHealthcareReviewsDashboard/HealthcareReviewsAnalysis?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

### Project Pipeline
```
Raw Data
   │
   ▼
Preprocessing
   ├─ Cleaning
   ├─ Tokenisation
   └─ Lemmatisation
   │
   ▼
Topic Modeling
   └─ Model Evaluation (BERTopic VS LDA)
   │
   ▼
Optimised Model
   └─ Grid Search
   │
   ▼
Post-processing
   ├─ Extract Representative Reviews
   ├─ Translate to English
   ├─ Summarise Translated Reviews
   └─ Extract Keywords
   │
   ▼
Presentation
   └─ Tableau Dashboard
```
   

## Purpose & Motivation
Understanding patient experience is critical for improving healthcare quality. However, suitable English-language datasets of healthcare facility reviews were not available for this analysis. Thus, this Russian-language dataset was identified as the closest viable alternative.

This project addresses that constraint by:
- Translating Russian healthcare reviews into English
- Extracting dominant themes using topic modelling
- Generating representative summaries and keywords for interpretability
- Visualising insights in an interactive Tableau dashboard

## Dashboard Features
| Feature | Description |
|--------|------------|
| **KPI Cards** | Show total, positive, and negative review counts for quick high-level insights. |
| **Keyword Bubble Chart** | Visualises the top 5 keywords per topic; bubble size reflects topic review count. |
| **Topic Frequency Bar Chart** | Displays all topics ranked by number of representative reviews, highlighting dominant themes. |
| **Sentiment Distribution** | Shows percentage breakdown of positive, negative, and neutral reviews for each topic. |
| **Count vs Negativity Scatterplot** | Compares review volume (count) against negativity scores to identify problem areas. |
| **Dynamic Filters / Selection** | Allows users to filter by topic for interactive exploration. |
| **Representative Review Panels** | Summarises key reviews for each topic, providing qualitative insights alongside quantitative metrics. |


## Technical Features
- **Preprocessing:** Cleaning, tokenisation and lemmatisation of Russian reviews using NLTK (stopwords removal) and Natasha (lemmatisation).
- **Topic Modeling:** Benchmarked BERTopic against LDA, optimising LDA as best model with 20% Coherence Score baseline improvement.
- **Translation Pipeline:** Translated top 10 topic representative Russian reviews to English using Helsinki-NLP transformer model.
- **Review Summarisation:** Summarised translated reviews using DistilBART.
- **Keyword Extraction:** Top 5 most meaningful terms manually curated, as automated methods (TF-IDF and KeyBERT) did not produce sufficiently meaningful results.

## Tech Stack
- **Python/Pandas**: Data wrangling and feature engineering
- **Jupyter Notebook**: Development and analysis
- **HuggingFace Transformers**: Translation and summarisation models
- **NLTK**: For Russian Stopwords
- **Natasha**: Russian NLP
- **Tableau**: Dashboard visualisation
- **Git & GitHub**: Version control

## Prerequisites
- Python 3.8 or higher
- pip package manager

## Dataset
**Original Size:** 70,597 Russian-language healthcare reviews
**Project Sample:** 10,000 reviews
**Domain:** Patient experience — covering doctors, facilities, wait times, treatment, and staff

**Why Russian?**
No suitable English-language dataset meeting project criteria was available. Translation was integrated to bridge the language barrier and expand analytical accessibility.

## Repository Structure
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
### Top 10 Topics Identified
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

### Representative Review Summary and Top 5 Keywords
> A friend of ours died yesterday in ICU, and he was transferred from another hospital to a neuroanimation . The department doesn't pick up the phone, and the reception room won't help, he writes . "There's no way to know the state of the patient," he says . "What's going on outside the resuscitation room, it's impossible to know and understand, isolation is worse than in prison" 

1. Unreachable Doctors
2. Poor Communication
3. Delayed Emergency Care
4. Inadequate Staff Response
5. Patient Safety Risk

### Why this matters
- Topic Modeling surfaces the most discussed areas of patient experience without manually reading thousands of reviews
- Summaries ground the analysis in real patient language, making findings relatable and reportable
- Translation removes the language barrier entirely, making the dataset usable for English-speaking researchers and institutions
- Keywords allow for high-level thematic abstraction for quick insight communication

## Installation & Usage
1. Clone the repository:
```
git clone https://github.com/nayc-599/Multilingual-Healthcare-Review-Dashboard.git
cd Multilingual-Healthcare-Review-Dashboard
```
2. Install dependencies:
```
pip install -r requirements.txt
```
3. Open notebooks.
4. Run notebooks in order.

## Future Improvements
- Expand reviews lanaguage coverage
- Automate keyword extraction
- Automate NLP pipeline using cloud infrastructure (AWS)

## Author
- **GitHub:** [@nayc-599](https://github.com/nayc-599)
- **Email:** naychi1301@gmail.com

## Acknowledgement
- **Data Source**: [https://huggingface.co/datasets/blinoff/healthcare_facilities_reviews]

## Licence
MIT

