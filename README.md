# Restaurant Feedback Analyzer

**Team AIML-02** · Internectual Project Team · Sprint 2026-11-16 to 2026-11-22

## Client: Spice Route Kitchens

Spice Route Kitchens is a popular chain of Indian restaurants facing challenges in understanding customer satisfaction and identifying areas for improvement from the vast amount of online feedback. They need an automated system to analyze customer reviews, pinpoint common themes, measure sentiment, and generate actionable reports. This initial sprint focuses on building the foundational data pipeline and a basic analysis report.

**Sprint goal:** Process customer feedback data to extract sentiment and generate actionable insights for a local restaurant chain.

## Team and parts

- **Nandini M C**: Data Ingestion & Integration (integration owner this week)

- **Harini K**: Feature Engineering & Basic Analysis

- **Niyati Bansal**: Reporting & Visualization

## Contract between the parts

## Repository Structure
```
.gitignore
README.md
requirements.txt

├── data_ingestion/
│   ├── raw_feedback.csv             # Sample raw input data
│   └── ingest_clean.py              # Script to clean raw feedback
│
├── feature_analysis/
│   └── analyze_features.py          # Script to extract sentiment and features
│
└── reporting/
    └── generate_report.py           # Script to create a summary report

└── integration/
    └── run_pipeline.py              # Orchestration script
    └── README.md                    # Main project README
```

## Interfaces

### 1. `data_ingestion/ingest_clean.py`
*   **Input**: `data_ingestion/raw_feedback.csv`
    *   CSV format with columns:
        *   `feedback_id` (string): Unique identifier for the feedback
        *   `date` (string): Date of the feedback (YYYY-MM-DD)
        *   `restaurant_id` (string): Identifier for the restaurant branch
        *   `customer_id` (string): Identifier for the customer
        *   `feedback_text` (string): The actual customer review text
        *   `rating` (integer): Rating given by the customer (1-5)
*   **Output**: `data_ingestion/cleaned_feedback.csv`
    *   CSV format with columns:
        *   `feedback_id` (string)
        *   `feedback_text` (string)
        *   `rating` (integer)
        *   `cleaned_text` (string): Lowercased, stripped of punctuation and extra spaces.

### 2. `feature_analysis/analyze_features.py`
*   **Input**: `feature_analysis/cleaned_feedback.csv`
    *   CSV format, same as `data_ingestion/cleaned_feedback.csv` output.
*   **Output**: `feature_analysis/analyzed_feedback.csv`
    *   CSV format with columns:
        *   `feedback_id` (string)
        *   `cleaned_text` (string)
        *   `rating` (integer)
        *   `sentiment_score` (float): A numerical score indicating sentiment (e.g., -1 to 1).
        *   `positive_keywords` (string): Comma-separated list of identified positive keywords.
        *   `negative_keywords` (string): Comma-separated list of identified negative keywords.

### 3. `reporting/generate_report.py`
*   **Input**: `reporting/analyzed_feedback.csv`
    *   CSV format, same as `feature_analysis/analyzed_feedback.csv` output.
*   **Output**: `reporting/summary_report.txt`
    *   A plain text file summarizing key findings, e.g., overall average rating, top 5 most frequent positive/negative keywords, and a few example positive/negative feedback snippets.

## How to Run the Product
1.  **Clone the repository:** `git clone <repo_url>`
2.  **Navigate to the project root:** `cd <project_folder>`
3.  **Create and activate a virtual environment:**
    `python3 -m venv venv`
    `source venv/bin/activate` (Linux/macOS) or `.\venv\Scripts\activate` (Windows PowerShell)
4.  **Install dependencies:** `pip install -r requirements.txt`
5.  **Run the full pipeline:** `python integration/run_pipeline.py`
    This script will orchestrate the execution of `ingest_clean.py`, `analyze_features.py`, and `generate_report.py` in sequence, copying intermediate files as needed between the respective module folders.
6.  **View results:** Check `reporting/summary_report.txt` for the generated report and the deployed live demo link in `integration/README.md` (after Nandini's integration ticket is complete).


## How we work

1. Create a branch named after your ticket key (for example `aiml-07-w5-02`). Never push directly to `main`.

2. Build your ticket in your part's folder. Commit often with clear messages.

3. Open a pull request into `main` and submit the PR link on your ticket in the Internectual workspace.

4. Review one teammate's pull request every week (comment and approve).

5. The integration owner merges approved pull requests, makes everything run together, updates this README with run steps and the live demo link.



_This repository is private during the sprint and becomes public afterwards so you can show it in your portfolio._