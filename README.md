# Credit Card Fraud Detection – Model Evaluation

## 1. Comparative Performance of Machine Learning Models

The performance of nine machine learning models was evaluated using Accuracy, Precision, Recall, and F1-Score.

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| Random Forest | 99.956% | 0.97 | 0.77 | **0.86** |
| K-Nearest Neighbors (KNN) | 99.953% | 0.94 | 0.78 | **0.85** |
| Support Vector Machine (SVM) | 99.932% | 0.97 | 0.62 | 0.76 |
| Decision Tree | 99.905% | 0.70 | 0.80 | 0.74 |
| Logistic Regression | 99.895% | 0.83 | 0.49 | 0.62 |
| Linear Regression | 99.888% | N/A | N/A | N/A |
| Ridge Regression | 99.888% | N/A | N/A | N/A |
| Lasso Regression | 99.875% | N/A | N/A | N/A |
| Gaussian Naive Bayes | 99.301% | 0.63 | 0.15 | 0.24 |

### Overall Observation

Among the evaluated models, **Random Forest achieved the highest F1-Score of 0.86**, making it the strongest overall model for identifying fraudulent transactions. **KNN followed closely with an F1-Score of 0.85**.

Although all models achieved accuracy above 99%, accuracy alone is not a reliable indicator of fraud-detection performance because of the severe class imbalance in the dataset.

---

## 2. Effect of Class Imbalance

The test dataset contains:

- **56,864 legitimate transactions**
- **98 fraudulent transactions**

Fraudulent transactions represent only a very small portion of the dataset.

Because of this imbalance, a model that predicts every transaction as legitimate could still achieve approximately **99.82% accuracy**.

Therefore, accuracy can be misleading for this problem. More importance should be given to:

- **Precision** – How many transactions predicted as fraud are actually fraudulent?
- **Recall** – How many of the actual fraudulent transactions were successfully detected?
- **F1-Score** – Provides a balance between precision and recall.

Thus, **F1-Score, Recall, and Precision are more meaningful evaluation metrics than accuracy** for this application.

---

## 3. Analysis of High-Performing Models

### Random Forest

Random Forest achieved the best overall performance with an **F1-Score of 0.86**, along with a **precision of 0.97** and **recall of 0.77**.

Its strong performance can be attributed to its ability to model complex and non-linear relationships between transaction features. Since it combines multiple decision trees, it can produce robust predictions without relying on a single decision boundary.

### K-Nearest Neighbors (KNN)

KNN achieved an **F1-Score of 0.85**, making it the second-best model.

The use of `StandardScaler` helps KNN because the algorithm relies on distances between data points. Scaling the features ensures that features with larger numerical ranges do not dominate the distance calculation.

KNN achieved a **recall of 0.78**, slightly higher than Random Forest, indicating that it detected a larger proportion of fraudulent transactions.

### Support Vector Machine (SVM)

SVM obtained an **F1-Score of 0.76**, with a very high **precision of 0.97** but a relatively lower **recall of 0.62**.

This means SVM is highly accurate when it predicts a transaction as fraudulent, resulting in fewer false fraud alerts. However, it fails to detect some actual fraudulent transactions.

---

## 4. Analysis of Lower-Performing Models

### Gaussian Naive Bayes

Gaussian Naive Bayes recorded the lowest fraud-detection performance, with an **F1-Score of 0.24** and a **recall of 0.15**.

The primary reason is the model's assumption that features are conditionally independent given the class. In a real-world credit card dataset, transaction features may have relationships with each other, and their distributions may not follow the assumptions required by Gaussian Naive Bayes.

As a result, the model struggles to correctly identify fraudulent transactions.

### Linear, Ridge, and Lasso Regression

Linear Regression, Ridge Regression, and Lasso Regression achieved high accuracy but were not evaluated using standard classification metrics such as Precision, Recall, and F1-Score.

These regression models were converted into binary predictions using a **0.5 threshold**. This approach creates a relatively simple linear decision boundary, which is not well suited to the complex and non-linear nature of fraud detection.

Consequently, their high accuracy should **not** be interpreted as evidence of superior fraud-detection capability.

---

## 5. Final Conclusion

The comparative analysis shows that **Random Forest is the most suitable model among the nine evaluated approaches**, achieving the highest **F1-Score of 0.86** and a **precision of 0.97**.

KNN also performed very well, particularly in terms of recall, while SVM demonstrated excellent precision but comparatively lower recall.

The results highlight an important characteristic of fraud detection:

> **High accuracy does not necessarily mean effective fraud detection.**

Due to the severe class imbalance, models must be assessed primarily using **Precision, Recall, and F1-Score**.

### Fraud-Detection Performance Ranking

**Random Forest (0.86) > KNN (0.85) > SVM (0.76) > Decision Tree (0.74) > Logistic Regression (0.62) > Gaussian Naive Bayes (0.24)**

### Best Model

**Random Forest**

- Accuracy: **99.956%**
- Precision: **0.97**
- Recall: **
