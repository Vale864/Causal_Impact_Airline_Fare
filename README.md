# Executive Summary

### Project Overview
In 2012, Delta Air Lines introduced "Basic Economy," a strategic segmentation product designed to compete with Low-Cost Carriers (LCCs) like Spirit without cannibalizing premium revenue.

This project employs Bayesian Causal Inference to quantify the financial impact of this decision. Unlike a standard A/B test, this policy was rolled out widely, making it a complex observational study requiring rigorous counterfactual modeling to isolate the true treatment effect from market noise.

### STAR Breakdown

* **Situation:** The airline industry faced a paradigm shift in 2012 as legacy carriers struggled to compete with LCCs on price. Delta needed a way to segment price-sensitive customers without lowering prices across the board.

* **Task:** My objective was to rigorously determine if Basic Economy caused a credible lift in revenue and yield, or if observed growth was merely a result of post-recession economic recovery.

* **Action:**
    * **Data Engineering:** Extracted and processed millions of rows of flight data from the US Department of Transportation's DB1B (Airline Origin and Destination Survey) dataset.
    * **Modeling:** Implemented a Bayesian Structural Time Series (BSTS) model using PyMC to construct a dynamic counterfactual based on pre-treatment trends and seasonality.
    * **Validation:** Utilized a Multivariate Synthetic Control (SCM) as a secondary validation method, creating a weighted "Synthetic Delta" from a donor pool of untreated competitor routes. Robustly controlling for economic confounders, the SCM model estimated a 3.6% lift in yield while preserving market share (+0.43pp) averaged across all treated routes.

* **Result:** The analysis confirmed the strategy was highly accretive and competitively effective. Results for the DTW-FLL route:
    * **Revenue Lift:** Estimated a 1.8 million cumulative revenue increase over the treatment period against the counterfactual, with an average quarterly lift of ~200,494k.
    * **Statistical Certainty:** The model produced a >99.9% probability of positive impact, with the 94% High Density Interval (HDI) remaining strictly positive [927k, 1.76M].
    * **Competitive Defense:** Simultaneously identified a 0.63 million revenue contraction for the primary competitor (Spirit) on the same route, indicating the strategy successfully diverted price-sensitive demand away from the LCCs.

### Tech Stack
* **Language:** Python 3.10+
* **Libraries:** PyMC, ArviZ, Pandas, NumPy, Matplotlib/Seaborn
* **Data Source:** US DOT DB1B Market Data

### Methodology Note
Why **PyMC**? Standard regression techniques often fail to account for the temporal structure and evolving variance of airline data. By using a Bayesian approach, I generated **Credible Intervals** (uncertainty bands) around the impact estimates, yielding a more robust risk assessment than simple point estimates.

---
*Author: Austin Woolston*
*Connect with me on [LinkedIn](www.linkedin.com/in/austin-woolston-0a3a1a255)*

---
