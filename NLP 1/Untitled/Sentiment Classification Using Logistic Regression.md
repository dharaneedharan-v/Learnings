## 📘 What is Regression?

**Regression** is a type of **supervised machine learning** used to **predict a value** based on past data.

### 🔍 Purpose:

To find the relationship between **input (independent)** variables and an **output (dependent)** variable.

---

### 🎯 Example:

Imagine you're predicting the **price of a house** based on its **size (in square feet)**.

|Size (sq ft)|Price ($)|
|---|---|
|1000|150,000|
|1500|200,000|
|2000|250,000|

You can draw a straight line that best fits these points.

This line is the **regression line**, and it helps you **predict the price** of a new house.

> 🧠 If someone says the house is 1,800 sq ft, regression can predict the likely price (e.g., $230,000).

---

## 🔢 Types of Regression

|Type|Use Case|
|---|---|
|**Linear Regression**|Predict continuous values (e.g., prices, scores)|
|**Logistic Regression**|Predict probabilities for categories (e.g., spam or not)|
|**Polynomial Regression**|Captures curves instead of straight lines|
|**Ridge / Lasso**|Regularized linear regression (to avoid overfitting)|

---

## 🧠 Summary:

> **Regression is used to predict values** based on known data. It finds patterns between variables.

## 📘 Differences Between **Linear** and **Logistic** Regression

|Feature|**Linear Regression**|**Logistic Regression**|
|---|---|---|
|**Purpose**|Predict **continuous** numeric values|Predict **categorical** outcomes (e.g. yes/no)|
|**Type of Output**|Any real number (e.g., price = 215.3)|Probability between 0 and 1 (e.g., spam = 0.87)|
|**Algorithm Type**|Regression|Classification|
|**Equation**|y=b0+b1xy = b_0 + b_1xy=b0​+b1​x|P(y=1)=11+e−(b0+b1x)P(y=1) = \frac{1}{1 + e^{-(b_0 + b_1x)}}P(y=1)=1+e−(b0​+b1​x)1​|
|**Target Variable (y)**|Continuous|Binary or categorical (0/1 or Yes/No)|
|**Output Interpretation**|Direct value prediction|Probability of class membership (then thresholded)|
|**Loss Function**|Mean Squared Error (MSE)|Log Loss (Cross Entropy)|
|**Linearity of Relationship**|Assumes **linear** relationship between x and y|Assumes **log-odds** of y is linear in x|
|**Use Case Example**|Predict house price, temperature, etc.|Predict spam/ham, pass/fail, disease/no disease|

---

## 🔍 Real-World Examples

|Task|Use Which Model?|Why?|
|---|---|---|
|Predict student scores|**Linear Regression**|Output is a numeric score (e.g., 82.5)|
|Predict if email is spam|**Logistic Regression**|Output is a yes/no (1/0) classification|
|Predict sales next week|**Linear Regression**|Continuous outcome (sales amount)|
|Predict if loan will default|**Logistic Regression**|Binary outcome (default or not)|

---

## 🧠 Easy Way to Remember:

- **Linear Regression** = Predict numbers
    
- **Logistic Regression** = Predict **probability** of a **class**


### ✅ What is Logistic Regression? Sentiment Classification Using Logistic Regression

Logistic Regression is a **supervised learning algorithm** used for **binary classification** — meaning, it helps us decide between **two classes**, like:

- Positive vs Negative
    
- Spam vs Not Spam
    
- Yes vs No
    

Even though it's called **regression**, it’s actually used for **classification**.

---

### 💬 What is Sentiment Classification?

Sentiment Classification means using a machine learning model to **detect the emotion or opinion** in text — usually:

- **Positive**
    
- **Negative**
    
- (Sometimes **Neutral** too)
    

Example:

|Review|Sentiment|
|---|---|
|“I love this movie!”|Positive|
|“The plot was boring and slow.”|Negative|

---

## 🧪 How Logistic Regression Helps in Sentiment Analysis

Here’s how it works step by step:

---

### 1. **Feature Extraction (Convert Text to Numbers)**

You can't feed raw text into a model, so first we convert it using:

- **Bag of Words**
    
- **TF-IDF (Term Frequency–Inverse Document Frequency)**
    
- **Word Embeddings (optional for advanced models)**
    

> Example:  
> "I love this movie" → `I:1, love:1, this:1, movie:1`

---

### 2. **Model Learning (Training Logistic Regression)**

The model learns to associate **certain words or patterns** with positive or negative labels.

It fits a **logistic function (sigmoid)**:

$$
P(y=1∣x)=1+e−(b0​+b1​x1​+b2​x2​+⋯+bn​xn​)1​
$$

This outputs a **probability** between 0 and 1.

- If output > 0.5 → Class 1 (Positive)
    
- If output < 0.5 → Class 0 (Negative)
    

---

### 3. **Prediction**

Once trained, the model can predict sentiment for new reviews.

> Input: "This phone is amazing"  
> Output: 0.92 → **Positive**

---

## 🔍 Why Use Logistic Regression for Sentiment Classification?

|Advantage|Reason|
|---|---|
|Simple and Fast|Easy to train and interpret|
|Works Well with High-Dimensional Data|Like Bag of Words and TF-IDF|
|Outputs Probability|Helps in ranking or thresholding|
|Baseline for More Complex Models|Before using SVM, Neural Nets, etc.|

---

## 📌 Summary Table

|Aspect|Logistic Regression for Sentiment|
|---|---|
|Type|Binary Classification|
|Input|Text (converted to numbers)|
|Output|Probability (0–1)|
|Final Label|Positive / Negative|
|Feature Methods|Bag of Words, TF-IDF|
|Evaluation|Accuracy, Precision, Recall, F1|