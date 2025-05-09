# Spambase Dataset: Spam or Not Spam E-mails Using LGBM
Hans Darmawan - JCDS2602

---

## 1. Business Understanding  
Email spam presents significant challenges, including financial loss, wasted time, and security risks. Among classification errors, false negatives—where spam emails are missed—are the most costly. The estimated cost per missed spam email is $175. Therefore, the primary business goal is to reduce false negatives by maximizing the model’s recall. This focus ensures that harmful spam is effectively identified and blocked, minimizing potential damage. It is also important to communicate the trade-offs between false positives and false negatives to stakeholders for informed decision-making.

---

## 2. Data Understanding  
The Spambase dataset contains 4,601 emails with 57 features related to word and character frequencies and capitalization patterns. The dataset is relatively balanced, with about 60% non-spam and 40% spam emails, which allows standard classification methods without complex imbalance handling. Exploratory analysis revealed that spam emails often contain specific words like “free” and “remove,” more special characters such as “!” and “$,” and longer sequences of capital letters. These features show stronger correlations with spam than overall word frequency. The data also exhibit skewness and outliers, especially in capitalization features, which should be considered in modeling.

---

## 3. Data Preparation  
Clear and descriptive feature names were established by renaming columns containing special characters. The dataset was split into training and testing subsets using stratification to preserve class distributions. This approach ensures that both subsets reflect the original balance of spam and non-spam emails, which is crucial for reliable model training and evaluation. Further preprocessing steps, such as handling duplicates and outliers, may enhance model performance and robustness.

---

## 4. Modeling  
Several ensemble classifiers were evaluated using five-fold cross-validation with recall as the performance metric. LightGBM demonstrated the highest average recall, closely followed by XGBoost. Hyperparameter tuning of LightGBM resulted in a model with slightly improved recall during cross-validation, though a minor decrease was observed on the test set. Despite this, the tuned model likely benefits from better generalization and regularization. Robust scaling was applied to mitigate the impact of outliers. LightGBM is recommended as the primary model for this task due to its strong recall and computational efficiency.

---

## 5. Evaluation  
The default LightGBM model achieved a recall of 0.945 on the test data, indicating a high rate of correctly identified spam emails. The tuned model’s recall was slightly lower at 0.941, with a small increase in false negatives. Confusion matrix analysis confirmed that both models effectively minimize missed spam. SHAP analysis provided interpretable insights, showing that certain words and capitalization patterns significantly influence predictions. Financial analysis demonstrated a 94.49% reduction in expected loss when using the model compared to no filtering. These results highlight the model’s practical value in reducing spam-related risks and costs.

---

## 6. Deployment  
The best-performing LightGBM model was saved for future use, enabling easy deployment and reproducibility. Persisting the model allows integration into production environments where it can provide real-time spam detection. It is advisable to implement monitoring for performance degradation and data drift post-deployment. Regular retraining should be scheduled to maintain effectiveness. Incorporating explainability tools will support transparency and user trust. Additionally, compliance with data privacy and security standards must be ensured when handling email data in operational settings.

---