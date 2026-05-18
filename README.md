# Employee Retention & Sentiment Analysis Pipeline

An end-to-end data science and machine learning pipeline designed to monitor corporate communication channels, measure employee engagement dynamics, track sentiment trends over time, and predict organizational flight risks before they impact team stability.

## Executive Summary
This project analyzes internal text communication data to provide senior leadership with clear, quantitative insights into workplace culture, employee sentiment shifts, and retention vulnerabilities. By processing corporate communication text through state-of-the-art Natural Language Processing (NLP) models, calculating multi-tiered risk vectors, and deploying machine learning classification algorithms, this pipeline transitions human resources strategies from reactive problem-solving to proactive, data-driven workforce planning.

---

## Executive Analytical Dashboard

Based on the completed data engineering and modeling tasks, the company-wide organizational analysis yields the following high-level performance and risk distribution profiles:

### 1. Sentiment-Based Leaderboard
Derived from the Task 3/Task 4 temporal aggregation and scoring algorithms, the employees demonstrating the highest positive and negative workplace interactions are:

* **Top 3 Most Positive Employees:**
    1. johnny.palmer@enron.com (Score: 3)
    2. lydia.delgado@enron.com (Score: -1)
    3. sally.beck@enron.com (Score: -13)
* **Top 3 Most Negative Employees:**
    1. don.baughman@enron.com (Score: -36)
    2. john.arnold@enron.com (Score: -35)
    3. bobette.riner@ipgdirect.com (Score: -32)

### 2. High-Priority Flight Risk Flags
Using the strict, company-defined criteria from **Task 5** (any employee triggering 4 or more negative communications within an independent, rolling 30-day window, regardless of their aggregate score), the following individuals have been officially flagged as **Active Retention Risks**:
* patti.thompson@enron.com
* eric.bass@enron.com
* rhonda.denton@enron.com
* kayne.coulter@enron.com
* lydia.delgado@enron.com
* don.baughman@enron.com
* john.arnold@enron.com
* bobette.riner@ipgdirect.com
* johnny.palmer@enron.com
* * **Note: all employees (using the given criteria) were flagged as **Active Retention Risks**

---

## Key Insights & Recommendations

* **The "Volume over Score" Paradox:** Broad monthly averages flatten out data and hide sudden spikes in negativity. Employees with decent overall monthly scores frequently triggered the 4-negative-email rule due to concentrated, stressful weeks.
  *  **Recommendation:** Avoid relying solely on monthly or quarterly averages; use rolling 30-day monitoring to trap high-risk behavioral changes early.
* **Model Sensitivity to Communication Nuance:** During the pipeline evaluation, short-form text and colloquial workplace slang (e.g., abbreviations, compressed status updates) frequently resulted in lower sentiment model confidence scores, filtering them below the 0.70 threshold into the "Neutral" category.
    * **Recommendation:** Implement a targeted enterprise text-cleaning dictionary prior to NLP modeling to expand model understanding of specialized workplace colloquialisms.
* **Predictive Model Adaptability (The Median Fix):** Because the highly localized test dataset initially flagged all observed samples as operational risks based on company rules, standard machine learning classifiers encountered a zero-variance learning ceiling (all positive targets). Implementing **Dynamic Thresholding via a Median-Split** broke this bottleneck, separating standard negative trends from extreme baseline behavior and enabling the classification algorithm to train successfully.
    * **Recommendation:** Scale this dynamic threshold mapping as the pipeline expands to larger production systems to ensure model robustness under varying baseline company stress levels.

---
