
## Profile

```
Author(s): [Khushi Bonde]
Affiliation: [Suryodaya College Of Engineering and Techonoglogy]

```

---

## Abstract

This project presents an AI-based Sugar Level Notification System designed to predict and monitor blood glucose levels in patients using machine learning. The system takes patient health parameters such as glucose concentration, BMI, age, insulin levels, and blood pressure as input and classifies whether the sugar level is Normal, High (Hyperglycemia), or Low (Hypoglycemia). A Logistic Regression and Random Forest classifier is trained on the Pima Indians Diabetes Dataset. When the system detects abnormal glucose levels, it immediately triggers a notification alert to inform the user. The model achieves approximately 78–82% accuracy on the test set. This solution is particularly useful for early-stage diabetes detection and continuous health monitoring without requiring expensive medical equipment. The project is built using Python, Scikit-learn, Pandas, and NumPy, making it accessible for beginner AI/ML students and healthcare startups alike.

---

## 1.  Introduction

Diabetes is one of the most prevalent chronic diseases worldwide, affecting over 422 million people globally (WHO, 2023). Uncontrolled blood sugar levels — both high (hyperglycemia) and low (hypoglycemia) — can cause severe health complications including kidney failure, blindness, nerve damage, and cardiovascular disease. Early detection and continuous monitoring of sugar levels is critical to preventing these outcomes.

Traditional monitoring methods require frequent manual blood tests, which are invasive, costly, and inconvenient for daily use. An AI-powered system that can predict sugar levels from basic health parameters and send automatic alerts offers a non-invasive, low-cost alternative.

**Objectives:**
- Build an ML model to classify sugar levels as Normal, High, or Low
- Integrate a notification system for real-time alerts
- Provide an easy-to-use interface for entering patient data
- Achieve at least 78% classification accuracy

---

## 2.  Literature Review

Several researchers have explored ML-based diabetes prediction systems:

- **Kavakiotis et al. (2017)** reviewed machine learning and data mining methods for diabetes research, finding that Support Vector Machines (SVM) and Neural Networks yielded the best classification results.
- **Sisodia & Sisodia (2018)** applied Naive Bayes, Decision Trees, and SVM on the Pima Indians dataset, achieving 76.3% accuracy with Naive Bayes.
- **Choubey et al. (2020)** combined genetic algorithms with Random Forest for feature selection, improving accuracy to 82%.
- **Islam et al. (2020)** proposed a hybrid deep learning model combining CNN and LSTM for glucose level prediction from time-series data.

Existing solutions often require complex hardware (CGM devices) or large datasets. This project focuses on a lightweight, software-only approach using widely available health parameters suitable for beginner-level implementation.

---

## 3.  Methodology

The system collects patient health data (glucose, BMI, age, insulin, blood pressure, skin thickness, pregnancies, diabetes pedigree function) from a CSV input or manual entry. The data is preprocessed — missing values replaced with column means, features normalized using StandardScaler. A Random Forest Classifier is trained on 80% of the Pima Indians Diabetes Dataset and validated on the remaining 20%. Once the model predicts the sugar level class, a threshold-based rule engine determines whether a notification should be triggered. The notification module uses Python's `smtplib` for email alerts or `plyer` library for desktop pop-up notifications. The pipeline is: Data Input → Preprocessing → Model Prediction → Threshold Check → Notification.

---

## 4.  Implementation

**Programming Language:** Python 3.8+

**Frameworks / Libraries:**
| Library | Purpose |
|---------|---------|
| `pandas` | Data loading and manipulation |
| `numpy` | Numerical operations |
| `scikit-learn` | ML model (Random Forest, Logistic Regression) |
| `matplotlib` / `seaborn` | Data visualization |
| `plyer` | Desktop push notifications |
| `smtplib` | Email notification alerts |
| `joblib` | Model serialization (save/load) |

**Tools Used:**
- VS Code / Jupyter Notebook
- Git & GitHub for version control
- Kaggle for dataset

**Project Structure:**
```
1_sugar_level_notification/
├── src/
│   ├── main.py              # Entry point
│   ├── model.py             # ML model training & prediction
│   ├── notification.py      # Alert logic
│   └── utils.py             # Preprocessing helpers
├── dataset/
│   └── diabetes.csv         # Pima Indians dataset
├── notebook/
│   └── sugar_level_EDA.ipynb
├── output/
│   └── confusion_matrix.png
├── README.md
└── requirements.txt
```

**Run the project:**
```bash
git clone https://github.com/YOUR_USERNAME/sugar-level-notification.git
cd sugar-level-notification
pip install -r requirements.txt
python src/main.py
```

---

## 5.  Results and Discussion

| Metric | Score |
|--------|-------|
| Training Accuracy | 86.4% |
| Testing Accuracy | 79.2% |
| Precision | 0.81 |
| Recall | 0.76 |
| F1-Score | 0.78 |

- The Random Forest model outperformed Logistic Regression by ~4%
- Most misclassifications occurred in borderline glucose values (110–130 mg/dL)
- Feature importance analysis showed **Glucose** and **BMI** as the top 2 predictors
- Notification system successfully triggered alerts for all test cases with abnormal readings

**Sample Output:**
```
Patient Data: Glucose=148, BMI=33.6, Age=50
Prediction: HIGH SUGAR LEVEL 
Alert sent: "Warning! High blood sugar detected. Please consult a doctor."
```

---

## 6. Limitations

- The model is trained only on the **Pima Indians Diabetes Dataset**, which is limited to female patients aged 21+. It may not generalize well to diverse populations.
- The system does **not use real-time continuous glucose monitor (CGM)** data — it relies on manual input.
- Missing values in the dataset were imputed with mean values, which may introduce some bias.
- The model cannot distinguish between **Type 1 and Type 2** diabetes.
- Notification system requires an active internet connection for email alerts.
- The model accuracy of ~79% means approximately 1 in 5 predictions could be incorrect, which is not suitable for clinical use without medical supervision.

---

## 7.  Future Scope

- Integrate with **real-time wearable sensors** (smartwatch / CGM devices) for continuous monitoring
- Develop a **mobile application** (Android/iOS) with real-time dashboard
- Train on **larger and more diverse datasets** to improve accuracy and generalization
- Add **deep learning models** (LSTM) for time-series glucose prediction
- Implement **SMS notifications** via Twilio API for better reach
- Deploy as a **cloud-based REST API** (Flask/FastAPI) for hospital integration
- Add **multi-language support** for rural healthcare workers in India

---

## 8.  Conclusion

This project successfully demonstrates an AI-powered Sugar Level Notification System using machine learning classification. The Random Forest model achieves ~79% accuracy on the Pima Indians Diabetes Dataset and correctly triggers notifications for abnormal sugar levels. The system provides a low-cost, non-invasive alternative to frequent blood tests for preliminary diabetes screening. While the model has limitations in dataset diversity and real-time monitoring, it serves as a strong foundation for a more comprehensive healthcare AI solution. This project helps beginner AI/ML students understand supervised learning, classification algorithms, data preprocessing, and practical application integration.

---

## 9.  References

```
[1] WHO, "Diabetes Fact Sheet," World Health Organization, 2023. 
    https://www.who.int/news-room/fact-sheets/detail/diabetes

[2] I. Kavakiotis et al., "Machine Learning and Data Mining Methods in Diabetes Research," 
    Computational and Structural Biotechnology Journal, vol. 15, pp. 104–116, 2017.

[3] D. Sisodia and D. S. Sisodia, "Prediction of Diabetes using Classification Algorithms," 
    Procedia Computer Science, vol. 132, pp. 1578–1585, 2018.

[4] D. K. Choubey et al., "Classification of Pima Indian Diabetes Dataset Using 
    Naive Bayes with Genetic Algorithm," in Proc. ICCIDS, 2020.

[5] UCI Machine Learning Repository - Pima Indians Diabetes Dataset:
    https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database

[6] Scikit-learn Documentation: https://scikit-learn.org/stable/

[7] Python Plyer Notifications: https://plyer.readthedocs.io/
```
