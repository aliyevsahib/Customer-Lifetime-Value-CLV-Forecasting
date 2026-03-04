# Customer-Lifetime-Value-CLV-Forecasting
A production-ready, two-stage XGBoost pipeline designed to forecast 90-day Customer Lifetime Value (CLV) by effectively managing zero-inflation and outlier distortion. This universal behavioural engine utilises advanced L1/L2 regularisation and threshold optimisation to deliver robust, deployment-ready customer insights.

📌 Project Overview
Predicting Customer Lifetime Value (CLV) is one of the most mathematically complex challenges in e-commerce due to Zero-Inflation (the vast majority of customers will not return to make another purchase) and Outlier Distortion (a tiny fraction of "Whale" customers account for massive revenue skew). This project demonstrates a production-ready, universal behavioural engine. By utilising a Two-Stage XGBoost Hurdle Model and rigorous mathematical regularisation, this pipeline identifies high-value customers and forecasts 90-day spending while intelligently filtering out the noise of extreme outliers.

🏗️ Architecture & Key Visualizations
The pipeline is built purely on universal e-commerce purchasing behaviours (RFM, payment preferences, device type, and engagement metrics), making it a plug-and-play architecture for any transactional dataset.

1. Mathematical Regularisation & Feature Selection
To isolate the true behavioural signals, the pipeline applies L1 (Lasso) and L2 (Ridge) regularisation. This step mathematically identifies which features actually drive revenue.

A) Coefficient Impact (Shrinkage Analysis)
This chart demonstrates how different algorithms treat the features. Notice how Lasso mathematically crushes non-predictive variables to zero, isolating the strongest behavioural drivers.

<img width="1053" height="790" alt="3" src="https://github.com/user-attachments/assets/5ec8850e-b4ff-48a4-9852-a7bc22499515" />

B) The Lasso Trajectory. The non-monotonic ("wavy") lines in the Lasso Path reveal the fierce mathematical competition between multi-collinear features as the penalty strength increases. Figure 2: The algorithmic path of feature selection. The vertical dashed line represents the optimal penalty (Lambda) found via Cross-Validation.

<img width="1089" height="690" alt="4" src="https://github.com/user-attachments/assets/0f8b4af5-23d6-4269-b1b5-f560af8e4169" />

2. Final Model Performance (Core Customers)
To prevent "Mega-Whales" (the top 10% of spenders) from completely destroying the Average Error calculations, the model is evaluated strictly on the 90% core customer base. The XGBoost Regressor uses an Absolute Error objective to optimise for the median customer.

<img width="714" height="731" alt="6" src="https://github.com/user-attachments/assets/49b04752-8e42-464b-bc1d-227af70e0690" />

📊 Final Diagnostic Report
The results below reflect the pipeline's performance on the 90% core customer base. By managing outliers mathematically, these metrics present a realistic view of how the model performs on everyday shoppers:

* **Classification Accuracy:** 56.1%
* **Classification Precision (Thresh: 0.465):** 53.8%
* **Classification Recall / Catch Rate (Thresh: 0.465):** 56.6%
* **Regression Median Error (MedAE):** 385.05 TL
* **Regression Average Error (MAE):** 755.81 TL

💡 Strategic Insights & Business Recommendations
Through rigorous error analysis and mathematical regularisation, this project uncovered several critical business realities:

1) The Signal Gap: Historical RFM and basic session data only provide enough mathematical signal for a ~56% classification accuracy. This proves that customer intent is driven by specific events outside of basic RFM metrics.
2) The Outlier Reality: The top 10% of customers spend exponentially more than the median. Deploying a single model trained on "everyone" will inevitably fail the "average" customer.
3) Future Roadmap for Production: To push prediction accuracy past the 70% threshold, the business must begin logging High-Intent Digital Telemetry (e.g., cart abandonment sequences, wishlist additions, and email click-through paths).

This pipeline is fully built, leak-proof, and completely ready to ingest high-signal data the moment it becomes available.

🛠️ How to Use This Template
Data Ingestion: Swap in your own e-commerce dataset in Step 2.
Run Pipeline: The code is completely dynamic; it will automatically handle feature encoding, standard scaling, and objective mapping.
Adjust Threshold: Utilise the ROC Curve analysis block to find the optimal decision boundary for your specific business requirements (optimising for Precision vs. Recall).

