Anomaly Detection for Credit Card Fraud
📌 Project Overview
This project focuses on building an unsupervised anomaly detection system to identify fraudulent credit card transactions. Fraud detection is a challenging problem due to the highly imbalanced nature of datasets (fraudulent cases are extremely rare compared to genuine ones).

Instead of relying on supervised methods that need labeled data, we use dimensionality reduction and reconstruction error to identify anomalies without labels.

📊 About the Dataset
A real dataset of anonymized credit card transactions made by European cardholders in September 2013.

Transactions are labeled as fraudulent or genuine (for evaluation purposes).

Contains 28 numerical features, with no categorical variables.

The features are not the original ones, but rather the output of PCA (Principal Component Analysis) performed on the raw dataset for privacy reasons.

👉 Download the dataset here https://drive.google.com/file/d/1hIOhGiMpa61-FKjn8hmWBvVPXbR3PSue/view?usp=sharing

💡 Why Anomaly Detection?
In real-world fraud detection:

Many fraudulent cases go undetected, leading to incomplete labels.

Fraud patterns evolve over time, which makes supervised models obsolete quickly.

Hence, unsupervised learning systems are crucial because they don’t rely heavily on labeled data.

Key assumptions:

Fraud is rare.

Fraudulent transactions are different from the majority (normal transactions).

The more anomalous a transaction is, the more likely it is fraudulent.

🔎 Methodology
Dimensionality Reduction
We apply PCA (Principal Component Analysis) to reduce the dimensionality of data.

PCA attempts to capture the most variance of the data while reconstructing it with minimal error.

However, moving to a lower-dimensional space means some information is lost, which results in reconstruction error.

Hyperparameter tuning:

If the number of components ≈ original features → almost zero reconstruction error.

If too few components → very high reconstruction error.

Choosing the right number of components is crucial.

Anomaly Score
We define an anomaly score based on reconstruction error:

Anomaly Score
Reconstruction Error (per transaction) Max-Min Range of Errors in Dataset Anomaly Score= Max-Min Range of Errors in Dataset Reconstruction Error (per transaction)​

Reconstruction error = sum of squared differences between the original feature matrix and the reconstructed matrix.

Scores are scaled between 0 and 1 for interpretability.

Higher score → higher likelihood of fraud.

Important Note
The dataset’s features are already PCA components.

Performing PCA again is not unusual — we simply treat the given PCA components as our “original features.”

📈 Evaluation
We use Precision-Recall curves to measure performance, since the dataset is highly imbalanced.

Metrics like Average Precision and Recall at top anomalies give insight into how well the model identifies fraud.

🚀 Next Steps
Experiment with different PCA components to optimize detection performance.

Compare PCA-based anomaly detection with other methods (Autoencoders, Isolation Forest, One-Class SVM).

Deploy the model for real-time fraud detection pipelines.
