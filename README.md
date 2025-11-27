Real-Time Transaction Fraud Detection API

Project Overview

This project implements a robust, machine learning-based system to detect fraudulent transactions in real-time, designed specifically for mobile financial platforms.

The core solution utilizes a complete data science pipeline—from advanced feature engineering to hyperparameter-tuned model deployment—to significantly improve fraud detection accuracy over traditional, rule-based systems.

🌟 Key Features

Model: XGBoost Classifier (Selected for its superior performance on imbalanced data).

Evaluation Focus: F1-Score ($\approx 0.88$) and Balanced Accuracy ($\approx 0.92$), as standard accuracy is misleading due to the high class imbalance (0.1% fraud).

Business Impact: The model is projected to reduce loss from undetected fraud (False Negatives) by over 98%, transforming the client's financial outcome.

Deployment: Model is exposed via a lightweight Flask API for real-time scoring.

🛠️ Technology Stack

Component

Technology Used

Role

Language

Python

Primary implementation language.

Model

XGBoost

Best-performing ensemble algorithm for classification.

Libraries

pandas, scikit-learn, joblib, flask

Data handling, ML pipeline, model persistence, and API framework.

Preprocessing

MinMaxScaler, OneHotEncoder

Ensures new data is transformed consistently with the training data.

⚙️ Code Flow and Deployment

The project flow is divided into two phases: Pipeline Development (notebook) and Real-Time Scoring (API).

Pipeline Training (transaction-fraud-detection-cycle1.ipynb):

Data is cleaned and transformed (e.g., column names changed to snake_case).

Key features are engineered (diff_new_old_balance, etc.).

XGBoost is trained and optimized.

The final model and preprocessing objects (MinMaxScaler, OneHotEncoder) are saved to disk as .joblib files.

Real-Time API (handler.py & Fraud.py):

Fraud.py contains the Fraud class, which is the complete prediction pipeline. It loads the saved preprocessing artifacts to ensure live data is prepared correctly.

handler.py uses Flask to create an endpoint (/fraud/predict). It loads the final XGBoost model and routes new, incoming JSON data through the Fraud class pipeline to get a real-time prediction.

💡 Future Scope

To make the system more robust and adaptive:

Adaptive Learning: Implement continuous model retraining to counter Concept Drift (the evolution of fraud tactics over time).

Explainable AI (XAI): Integrate XAI to provide transparent reasons for flagging a transaction, enhancing trust and auditability.

Edge Computing: Explore deploying lightweight models for instant checks directly on user devices to reduce latency.
