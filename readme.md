# Employee Sentiment Analysis

This project performs sentiment analysis on internal corporate email communications to detect engagement levels, identify flight risks, and build predictive models.

---

## 📁 Project Structure

```
Employee_Sentiment_Analysis/
├── employee_sentiment_analysis.ipynb     # Main Jupyter notebook
├── sentiment_labeled_data.csv            # Final sentiment-labeled dataset
├── labeled_sentiments_roberta.csv        # Raw model output before filtering or cleaning
├── monthly_employee_scores.csv           # Monthly sentiment score per employee
├── regression_features.csv               # Feature dataset used in regression model
├── visualizations.zip                    # All visualization images as PNGs
├── Final Report.pdf                      # Formal write-up of methodology and results
├── README.md                             # This file
```

---

## 🛠️ Setup Instructions

### 1. Clone the repository

```bash
git clone <repo-url>
cd Employee_Sentiment_Analysis
```

### 2. Create a virtual environment

```bash
conda create -n sentiment python=3.10
conda activate sentiment
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

#### Required packages:

- `transformers`
- `torch >= 2.6.0`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `nltk`

If using GPU, ensure compatible CUDA and torch versions (e.g., `torch==2.6.0+cu121`)

---

## ▶️ Usage

### Run the notebook

```bash
jupyter notebook employee_sentiment_analysis.ipynb
```

Make sure the data files (emails.csv or equivalent) are placed in the working directory.

### Outputs:

- `sentiment_labeled_data.csv`: each message labeled as Positive, Neutral, or Negative
- `labeled_sentiments_roberta.csv`: initial sentiment results from model
- `monthly_employee_scores.csv`: aggregate sentiment scores for each employee per month
- `regression_features.csv`: regression-ready feature data per employee per month
- `visualizations/`: sentiment distribution, temporal trends, rankings, etc.

---

## 📊 Methodology Overview

### 1. **Sentiment Classification**

- Used `cardiffnlp/twitter-roberta-base-sentiment` from Hugging Face Transformers.
- Each email’s `subject` and `body` were combined and passed through the model.
- Output mapped as:
  - `LABEL_0` → Negative
  - `LABEL_1` → Neutral
  - `LABEL_2` → Positive

### 2. **EDA & Visual Analysis**

- Count plots, pie charts, time series trends
- Message length vs sentiment comparisons

### 3. **Monthly Score Calculation**

- Sentiment scores assigned: +1 (Positive), 0 (Neutral), –1 (Negative)
- Aggregated per employee per month

### 4. **Ranking System**

- Top 3 and bottom 3 employees based on sentiment score
- Performed monthly

### 5. **Flight Risk Detection**

- Flagged employees sending ≥4 negative messages in any 30-day window
- Implemented with a sliding date window

### 6. **Predictive Modeling**

- Trained a linear regression model to predict monthly sentiment scores
- Features included message count, avg. length, sentiment ratios, etc.

---

## 📌 Submission Summary

The following files are included in the final submission ZIP:

- `employee_sentiment_analysis.ipynb`
- `Final Report.pdf`
- `README.md`
- `sentiment_labeled_data.csv`
- `labeled_sentiments_roberta.csv`
- `monthly_employee_scores.csv`
- `regression_features.csv`
- `visualizations.zip`

---

## 📬 Contact

For any questions, contact: [Your Name] | [[your.email@example.com](mailto\:your.email@example.com)]

---

**Status:** ✅ Completed

