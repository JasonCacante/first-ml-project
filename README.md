# Financial Risk Prediction Project 🧠💸

This project is focused on predicting financial risk using a machine learning model. The main objective is to reduce the credit default rate while maintaining financial inclusion for rural customers.

---

## ✅ Setup Checklist

### ✅ Setting up the environment

Created a Docker environment for the project and configured VSCode to work within the container.

```bash
# Build Docker image
docker build -t ml-project .

# Run Docker container
docker run --rm --name ml-project -p 8888:8888 -v $(pwd)/app:/app -td ml-project
```

---

### ✅ Setting up Git

Initialized a Git project and configured GPG commit signing.

Make sure to add the correct SSH key:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/your_ssh_key
```

---

### ✅ Setting up the CSV files

Using a dataset from Kaggle called **Financial Risk**. First, install the Kaggle library:

```bash
pip install kaggle
```

Download the `kaggle.json` authentication token and place it in:

```
~/.kaggle/kaggle.json
```

Then run:

```bash
#!/bin/bash
kaggle datasets download preethamgouda/financial-risk
```

After downloading, unzip the file.

---

## 📌 Project Scoping

### **Step 0: Problem Understanding**

- **What is the problem?**  
  The company faces a high risk of non-payment on financial credits, with a 10% portfolio risk threshold for profitability. The current risk level is 7%, nearing the limit.

- **Who does it impact and how much?**  
  - Impacts the company’s financial health and sustainability.  
  - Affects credit access for customers in rural areas.  
  - May result in stricter credit approval policies, limiting financial inclusion.

- **How is it being solved today?**  
  - Traditional credit scoring methods.  
  - Manual evaluation by risk analysts.  
  - Fixed rules based on income, employment status, and past credit history.

- **What are some of the gaps?**  
  - Lack of a dynamic risk assessment system.  
  - No predictive model to anticipate defaults.  
  - Possible biases in manual decision-making.

---

### **Step 1: Goals**

- **What are the goals of the project?**  
  - Develop a machine learning model to assess customer financial risk.  
  - Improve accuracy of risk prediction compared to current methods.  
  - Reduce default rate while maintaining financial inclusion.

- **How will we know if our project is successful?**  
  - Decrease in default rates below 7%.  
  - Model achieves high precision and recall in identifying high-risk customers.  
  - Business adoption and integration of model insights in credit approval.

---

### **Step 2: Actions**

- **What actions or interventions will this work inform?**  
  - Dynamic risk-based credit approval.  
  - Adjusted interest rates based on predicted risk.  
  - Early intervention strategies (e.g., reminders, financial education).

---

### **Step 3: Data**

- **What data do you have access to internally?**  
  - Customer credit history.  
  - Payment behavior.  
  - Loan terms and repayment details.  
  - Socioeconomic factors (if collected).

- **What data do you need?**  
  - Additional behavioral data (e.g., transaction history, spending habits).  
  - Alternative creditworthiness indicators (e.g., phone usage, utility payments).

- **What can you augment from external and/or public sources?**  
  - Credit bureau scores (if accessible).  
  - Economic indicators (e.g., inflation, unemployment rates).

---

### **Step 4: Analysis**

- **What analysis needs to be done?**  
  - **Prediction:** Develop a machine learning model to estimate probability of default.  
  - **Detection:** Identify key risk factors affecting customer non-payment.  
  - **Behavior change:** Suggest intervention strategies for high-risk customers.

- **How will the analysis be validated?**  
  - Train/test split on historical data.  
  - Cross-validation to ensure model robustness.  
  - Business validation through pilot implementation.

---

### **Ethical Considerations**

- **Privacy:** Ensure customer data protection and comply with regulations (e.g., GDPR, local laws).  
- **Transparency:** Make model decisions explainable to both customers and analysts.  
- **Discrimination/Equity:** Avoid biased decisions by auditing for fairness across demographics.  
- **Accountability:** Implement a feedback loop for model performance evaluation.

---

### **Additional Considerations**

- **Deployment:** Develop an API or dashboard for integration into the credit decision process.  
- **Field Evaluation:** A/B test model-based decisions against existing methods.  
- **Monitoring:** Regularly retrain and evaluate model performance to ensure long-term accuracy.

---

# 📊 Classification Results Explanation

### 🤖 Model Used
- **Random Forest Classifier** with 3 target classes:
  - **High**
  - **Medium**
  - **Low**

---

### 📈 Classification Report Output

| Class   | Precision | Recall | F1-Score | Support (True Samples) |
|---------|-----------|--------|----------|-------------------------|
| High    | 0.00      | 0.00   | 0.00     | 326                     |
| Medium  | 0.40      | 0.00   | 0.00     | 895                     |
| Low     | 0.59      | 1.00   | 0.74     | 1779                    |

- **Accuracy**: 0.59  
- **Macro Average F1-Score**: 0.25  
- **Weighted Average F1-Score**: 0.44

---

### 📉 Interpretation

- **High and Medium Risk Ratings were never predicted.**  
  This results in:
  - **Precision = 0.00**
  - **Recall = 0.00**
  - **F1-Score = 0.00**

- **All predictions were classified as 'Low'.**
  - The model achieved high recall for 'Low' (1.00) simply by predicting 'Low' for everything.

- **Sklearn Warning:**  
  You received the following:
  ```bash
  UndefinedMetricWarning: Precision is ill-defined and being set to 0.0 in labels with no predicted samples.

