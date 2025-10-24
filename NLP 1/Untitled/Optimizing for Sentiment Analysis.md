
## 🎯 1. **Understand the Goal of Sentiment Analysis**

Sentiment analysis is a **text classification task** where input text is categorized by emotional tone (positive/negative/neutral).

---

## 📦 2. **Pipeline for Sentiment Analysis (Must Know)**

### ➤ Step-by-step Process:

|Step|Explanation|
|---|---|
|**Text Collection**|e.g., Movie reviews, tweets|
|**Preprocessing**|Tokenization, lowercasing, stopword removal, stemming/lemmatization|
|**Feature Extraction**|Bag-of-Words, TF-IDF, Word Embeddings (Word2Vec, BERT)|
|**Model Training**|Naive Bayes, Logistic Regression, SVM, LSTM, etc.|
|**Evaluation**|Accuracy, Precision, Recall, F1-Score, Confusion Matrix|
## 🧠 1. **Text Vectorization Techniques** (Feature Extraction)

### ➤ **1.1. Bag-of-Words (BoW)**

- **What:** Counts frequency of each word.
    
- **Why Used:** Simple, fast, good for Naive Bayes and Logistic Regression.
    
- **Limitations:** No understanding of word meaning or order.
    

### ➤ **1.2. TF-IDF (Term Frequency – Inverse Document Frequency)**

- **What:** Weights important words (high frequency in one doc but rare overall).
    
- **Why Used:** Reduces impact of common words (e.g., "the", "is").
    
- **Good With:** Naive Bayes, SVM, Logistic Regression.
    
- **Not Used When:** You want deep context (e.g., sarcasm detection, semantics).
    

### ➤ **1.3. Word Embeddings (e.g., Word2Vec, GloVe)**

- **What:** Maps words to dense vectors based on meaning/context.
    
- **Why Used:** Captures word relationships, suitable for deep learning (LSTM, CNN).
    
- **Not Used With:** Naive Bayes – it expects count-based inputs, not continuous vectors.
    

### ➤ **1.4. Transformers (e.g., BERT)**

- **What:** Context-aware embeddings for each word (deep understanding).
    
- **Why Used:** State-of-the-art performance on sentiment tasks.
    
- **Not Used With:** Lightweight models (too heavy for basic classifiers like NB).
    

---

## 📦 2. **Naive Bayes Types (MultinomialNB, BernoulliNB, GaussianNB)**

|Type|Used For|Why / Why Not Used in Sentiment|
|---|---|---|
|**MultinomialNB**|Text classification|✅ Preferred for TF-IDF/BoW count features. Works with word frequencies.|
|**BernoulliNB**|Binary features (word exists or not)|❌ Less accurate in longer texts with varying word frequencies.|
|**GaussianNB**|Continuous numeric features|❌ Not for text. Used in image or sensor data (non-discrete).|

---

## **Common Models and Optimization Tips**

### 🔹 A. **Naive Bayes** (Great for text, fast, baseline)

- Use **MultinomialNB** for count-based features (Bag-of-Words or TF-IDF)
    
- Works well with short texts and sparse data
    
- Optimize using:
    
    - **Laplace smoothing (alpha)** to avoid zero probabilities
        
    - Feature selection (remove rare or common words)
        

### 🔹 B. **Logistic Regression** (Simple and powerful)

- Works well with TF-IDF
    
- Use **regularization (L1/L2)** to prevent overfitting
    
- Tune **C parameter** (inverse of regularization strength)
    

### 🔹 C. **SVM (Support Vector Machine)**

- Strong for high-dimensional text data
    
- Use **LinearSVC** for speed and scalability
    
- Tune **C** and **kernel** (use linear for text)
    

### 🔹 D. **Deep Learning (LSTM, BERT)** (Advanced)

- Better at capturing context and sequence
    
- Needs more data and compute
    
- Use **pretrained transformers** (like BERT) for accuracy



## 🧪 3. **Popular Classification Models for Sentiment**

|Model|Why Used in Sentiment|Why NOT Used Sometimes|
|---|---|---|
|**Naive Bayes**|Fast, works well with BoW/TF-IDF|Assumes independence, can miss word combinations.|
|**Logistic Regression**|Simple, interpretable|Struggles with non-linear patterns.|
|**SVM**|High-dimensional data, effective with TF-IDF|Slower with large datasets, not probabilistic.|
|**Random Forest**|Captures non-linear patterns|Slower and harder to interpret.|
|**LSTM (Deep Learning)**|Handles word order, context|Needs large dataset + compute.|
|**BERT (Transformer)**|Best accuracy, pre-trained knowledge|Very heavy, slow for real-time/simple tasks.|

---

## 📊 4. **Evaluation Metrics: When and Why**

|Metric|Use When…|Why|
|---|---|---|
|**Accuracy**|Balanced data|Simple overall measure.|
|**Precision**|False positives are costly|"Of those predicted positive, how many were right?"|
|**Recall**|False negatives are costly|"Of all actual positives, how many did we catch?"|
|**F1-Score**|Need balance (Precision + Recall)|Good for imbalanced classes.|
|**Confusion Matrix**|To visualize predictions|Helps spot specific types of errors.|

---

## 🔍 Summary: What to Use and When

|Task / Case|Recommended Tool / Reason|
|---|---|
|Short text, fast baseline|✅ Naive Bayes + TF-IDF (MultinomialNB)|
|Imbalanced data|✅ Logistic Regression + F1-Score|
|High accuracy, deep context|✅ BERT or LSTM (with embeddings)|
|Real-time application|✅ SVM or Logistic Regression|
|Interpretability important|✅ Logistic Regression or Decision Trees|
