# Social Media Sentiment Analysis using AI/NLP

An end-to-end **Data Analytics with AI** project that classifies social media posts into **Positive**, **Negative**, and **Neutral** sentiment using Natural Language Processing (NLP) and Machine Learning, with an accompanying Power BI-style dashboard for visual reporting.

> Submitted for the **AICTE | IBM SkillsBuild Data Analytics with AI Academic Internship 2026**, conducted by **BharatCares**.

---

## Project Description

Social media generates massive volumes of unstructured text every day. This project builds a pipeline that:

1. Loads and explores a dataset of social media posts (Twitter, Instagram, Facebook, YouTube).
2. Cleans and preprocesses raw text (removing URLs, mentions, punctuation, stopwords).
3. Converts text into numerical features using **TF-IDF vectorization**.
4. Trains and compares two ML classifiers — **Logistic Regression** and **Multinomial Naive Bayes**.
5. Evaluates models using accuracy, precision/recall, F1-score, and confusion matrices.
6. Exports predictions to a CSV for visualization in a **Power BI dashboard**.
7. Surfaces business insights (engagement patterns, platform-level sentiment, monthly trends).

**Best model accuracy:** ~96.8% (Logistic Regression on TF-IDF features)

## Dataset

- **File:** `social_media_sentiment_data.csv` (included in this repository, 2,020 rows)
- **Generation method:** Programmatically synthesized to simulate real-world social media posts across 4 platforms and 12 product/service topics, with realistic label noise (~4%) to reflect genuine annotation variance. This keeps the project fully self-contained and reproducible without external API keys.
- **To use real-world data instead**, swap in any public dataset with a `text` and `sentiment`/`label` column, for example:
  - [Sentiment140 (Kaggle)](https://www.kaggle.com/datasets/kazanova/sentiment140)
  - [Twitter US Airline Sentiment (Kaggle)](https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment)
  - Live data via the [Twitter/X API](https://developer.twitter.com/) or [Reddit API (PRAW)](https://praw.readthedocs.io/)

**Columns:** `post_id`, `date`, `platform`, `topic`, `text`, `likes`, `retweets`, `sentiment`

## Technologies Used

| Category | Tools |
|---|---|
| Language | Python 3.12 |
| Data handling | pandas, NumPy |
| NLP | Regex-based cleaning, TF-IDF (scikit-learn) |
| Machine Learning | scikit-learn (Logistic Regression, Multinomial Naive Bayes) |
| Visualization | Matplotlib, Seaborn |
| Dashboard / BI | Power BI (CSV import) — HTML dashboard included as an offline preview |
| Environment | Jupyter Notebook |

## Project Structure

```
├── YourName_ProjectName.ipynb          # Full project code (EDA, NLP, ML, evaluation)
├── requirements.txt                     # Python dependencies
├── YourName_ProjectReport.docx          # Full project documentation
├── README.md                            # This file
├── social_media_sentiment_data.csv      # Input dataset
├── sentiment_analysis_results.csv       # Model output (import this into Power BI)
└── Sentiment_Analysis_Dashboard.html    # Offline Power BI-style dashboard preview
```

## Setup & Run Instructions

1. **Clone/download** this project folder.
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```
4. Open `YourName_ProjectName.ipynb` and run all cells (**Cell → Run All**).
5. This generates `sentiment_analysis_results.csv` in the same folder.

## Building the Power BI Dashboard

1. Open **Power BI Desktop** → **Get Data** → **Text/CSV** → select `sentiment_analysis_results.csv`.
2. Create these visuals from the imported table:
   - **Donut chart** — `sentiment` (legend) vs. count of `post_id` → overall sentiment split
   - **Stacked column chart** — `platform` (axis), `sentiment` (legend), count of `post_id` → sentiment by platform
   - **Line chart** — `month` (axis), `sentiment` (legend), count of `post_id` → sentiment trend over time
   - **Bar chart** — average of `likes` by `sentiment` → engagement comparison
   - **KPI cards** — total posts, % positive, % negative, model accuracy (96.8%)
3. Use slicers on `platform` and `topic` for interactive filtering.
4. `Sentiment_Analysis_Dashboard.html` in this repo is an offline, browser-based preview of the same visuals (built with Chart.js) — open it directly in any browser, no installation required.

## Key Insights

- Positive sentiment is the largest share of posts, but Negative sentiment remains significant enough to warrant active monitoring.
- Positive posts receive roughly **2x the average engagement (likes)** compared to Neutral/Negative posts.
- Sentiment distribution varies by platform, useful for prioritizing community management effort.
- The trained model generalizes well (96.8% accuracy) and can be reused for real-time sentiment scoring on incoming posts.

## Author

**[Nikky Bharti]** — AICTE | IBM SkillsBuild Data Analytics with AI Internship 2026 (BharatCares)
