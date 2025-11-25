#  Causal Impact of Deltas Basic Economy Fare Class on Airline Market Dynamics

# Project Summary: TL;DR Version

**For a more detailed project summary with visualizations, please see airline_readme.ipynb**

### 📌 Project Overview
In 2012, Delta Airlines introduced "Basic Economy" fares—a restrictive fare class designed to compete with low-cost carriers like Spirit and Frontier without cannibalizing premium revenue.

This project uses **Bayesian Causal Inference** to quantify the impact of this strategic decision on Delta's KPIs: yield, market share, and revenue. Unlike a standard A/B test, this policy was rolled out widely, making it an observational study requiring rigorous counterfactual modeling.

### ⭐️ STAR Breakdown

* **Situation:** The airline industry faced a paradigm shift in 2012 as legacy carriers struggled to compete with Low-Cost Carriers (LCCs) on price. Delta needed a way to segment price-sensitive customers without lowering prices across the board.
* **Task:** My goal was to determine if the introduction of Basic Economy caused a statistically significant increase in the KPIs, or if observed growth was simply due to external market factors (e.g., post-recession recovery).
* **Action:** 
    * **Data Engineering:** Extracted and cleaned historical flight data from the US Department of Transportation's **DB1B (Airline Origin and Destination Survey)** dataset.
    * **Modeling:** Implemented a **Bayesian Structural Time Series (BSTS)** and **Multivariate Synthetic Control (SCM)** model using **PyMC**.
    * **Counterfactuals:** 
      * For the SCM, a synthetic control group was used to create a weighted combination of competitor metrics (airlines that did not introduce Basic Economy at that time) to predict what Delta's KPIs *would have been* without the policy.
      * For the BSTS, instead of creating a synthetic control from other routes, it creates a counterfactual solely based on the carrier's own pre-treatment history.

* **Result:** The models demonstrated a clear divergence between the actual observed KPIs and the counterfactuals, indicating a positive causal effect attributable to the segmentation strategy. Additionally, the BSTS model demonstrates that the strategy successfully rebuffed the low-cost carriers' encroachment into Delta's market share.

### 🛠 Tech Stack
* **Language:** Python 3.10+
* **Libraries:** PyMC, ArviZ, Pandas, NumPy, Matplotlib/Seaborn
* **Data Source:** US DOT DB1B Market Data

### 🧠 Methodology Note
Why **PyMC**? Standard regression techniques often fail to account for the temporal structure and evolving variance of airline data. By using a Bayesian approach, I generated **Credible Intervals** (uncertainty bands) around the impact estimates, providing a more robust risk assessment than simple point estimates alone.

---
*Author: Austin Woolston*
*Connect with me on [LinkedIn](https://www.linkedin.com/in/austin-woolston-0a3a1a255/)*

---
