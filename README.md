# PhishOFE: Phishing URL Detection & Evaluation Framework

PhishOFE is a machine learning–based cybersecurity system designed to **detect phishing URLs in real time** by analyzing URL structure, HTML content, and derived behavioral features.  
The system integrates **Principal Component Analysis (PCA)** for dimensionality reduction and a **CatBoost classifier** for robust, high-accuracy detection across real-world and adversarial scenarios.

---

## 🚀 Features

- 🌐 Real-time phishing URL detection  
- 🔍 URL-level, HTML-based, and derived feature extraction  
- 📉 PCA-based dimensionality reduction (8 components)  
- 🤖 Multi-model training with automatic best-model selection  
- ⚡ Fast inference suitable for real-time security systems  
- 🧪 Extensive testing: functional, adversarial, and stress cases  
- 📊 Confusion Matrix, ROC Curve, and AUC evaluation  

---

## 🧪 Dataset Overview

- Total Samples: **101,063 URLs**
- Classes: **2**
  - Legitimate: 51,572  
  - Phishing: 49,491  
- Original Features: **30**
- Feature Categories:
  - **URL-Level**: length, digits, symbols, subdomains, HTTPS usage
  - **HTML-Based**: forms, iframes, scripts, redirects, popups
  - **Derived Features**: URL complexity score, suspicious character ratio, content density

---

## 📉 PCA Dimensionality Reduction

- Number of Components: **8**
- Total Variance Retained: **52.95%**
- Benefit:
  - Reduced feature redundancy
  - Lower computational cost
  - Stable generalization performance

> PCA compresses high-dimensional features into compact representations while preserving the most discriminative phishing patterns.

---

## 📈 Model Comparison

Multiple models were trained on PCA-transformed features.  
**Best performing model: CatBoost**

| Model         | Accuracy | Precision | Recall | F1-Score |
|---------------|----------|-----------|--------|----------|
| Random Forest | 0.9546   | 0.9753    | 0.9309 | 0.9526   |
| XGBoost       | 0.9787   | 0.9845    | 0.9717 | 0.9781   |
| **CatBoost**  | **0.9797** | **0.9855** | **0.9729** | **0.9792** |

---

## 🧠 Final Model Performance (CatBoost)

- **Accuracy:** 97.97%  
- **F1-Score:** 0.9792  
- **ROC-AUC:** **0.9967**  
- **Overfitting Check:** No major gap between train and test performance  

### Confusion Matrix Summary

|                | Predicted Legit | Predicted Phishing |
|----------------|----------------|--------------------|
| **Actual Legit**     | 10,173         | 142                |
| **Actual Phishing** | 268            | 9,630              |

---

## 🧪 Robustness & Stress Testing

PhishOFE was evaluated against **realistic and adversarial URLs**, including:

- Empty strings and localhost URLs  
- Raw IP-based phishing links  
- URL shorteners  
- Homoglyph attacks (Unicode domain spoofing)  
- Encoded URLs  
- Enterprise SSO and complex legitimate domains  

> The model demonstrates strong phishing detection capability while maintaining reasonable confidence on complex legitimate URLs.

---

## 🔧 Tech Stack

| Layer             | Technology Used |
|------------------|-----------------|
| Language         | Python |
| Machine Learning | Scikit-learn, CatBoost, XGBoost |
| Feature Reduction| PCA |
| Web Parsing      | Requests, BeautifulSoup |
| Visualization    | Matplotlib, Seaborn |
| Environment      | Jupyter Notebook |

---

## 🏗 System Architecture

1. URL Input (Single / Batch)  
2. Feature Extraction (URL + HTML + Derived)  
3. Preprocessing & Scaling  
4. PCA Transformation (8 Components)  
5. Model Inference (CatBoost)  
6. Prediction with Probability Scores  
7. Evaluation & Visualization  

---

## ▶️ How to Run

```bash
git clone https://github.com/<your-username>/PhishOFE.git
cd PhishOFE
pip install -r requirements.txt
jupyter notebook phishOFE.ipynb
```

Test a URL:

```bash
detector.predict("https://example.com")
```

---

## 🧪 Example Output

```bash
Prediction           : Phishing
Phishing Probability : 0.99
Legitimate Probability : 0.01
```

---

## 📄 Full Project Report → `PhishOFE_Final_Report.docx`

👉 [Click here to view the report]([https://github.com/KushalManikonda/PhishOFE](https://github.com/KushalManikonda/PhishOFE/blob/main/PhishOFE_Final_Report.docx))

---

## 💻 GitHub Repository → `PhishOFE`

👉 [Click here to view the GitHub Repository](https://github.com/KushalManikonda/PhishOFE)
