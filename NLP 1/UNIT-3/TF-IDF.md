
## 📘 What is **TF-IDF**?

**TF-IDF** stands for:

- **TF** = Term Frequency
    
- **IDF** = Inverse Document Frequency
    

It’s a **numerical statistic** used to evaluate **how important a word is** in a document **relative to a collection of documents (corpus)**.

---

### 🧠 In Simple Terms:

> TF-IDF helps us know **which words are important and meaningful** in a document and **filters out common, unimportant words** like "the", "is", "and".

---

## 🎯 Why Do We Use TF-IDF?

|Purpose|Why It's Helpful|
|---|---|
|✅ Identify key words|It highlights important terms in documents|
|✅ Reduce noise|It downweights common, unimportant words|
|✅ Better than raw counts|It gives smarter weights than Bag of Words|
|✅ Improves NLP models|Helps in text classification, clustering, search|

---

## 🔍 How Does TF-IDF Work?

### Step 1: **TF – Term Frequency**

Measures how often a word appears in a document.

$$
TF=Number of times term t appears in document​ / Total number of terms in document​
$$

### Step 2: **IDF – Inverse Document Frequency**

Measures how **rare** or **unique** a word is across documents.

$$
IDF=log(Number of documents containing term )/ 
(Total number of documents​)
$$



### Step 3: **TF-IDF Score**
$$
TF-IDF(t,d)=TF(t,d)×IDF(t)
$$
---

## 💡 Intuition Example:

Let’s say you have 3 documents:

vbnet

CopyEdit

`Doc1: "cat sat on mat" Doc2: "dog sat on log" Doc3: "cat chased mouse"`

- Word **"sat"** appears in multiple docs → gets **low weight**
    
- Word **"mouse"** appears only once → gets **high weight**
    
- TF-IDF makes **"mouse"** more important than **"sat"**
    

---

## ⚙️ Where Is TF-IDF Used?

|NLP Task|How TF-IDF Helps|
|---|---|
|**Search engines**|Rank results based on word importance|
|**Text classification**|Select key features (words)|
|**Spam filtering**|Detect suspicious or rare terms|
|**Topic modeling**|Find dominant terms in documents|

---

## 🔄 Compared to Other Methods

|Method|Description|Limitations|
|---|---|---|
|**Bag of Words (BoW)**|Counts each word|Doesn’t consider importance or frequency across documents|
|**TF-IDF**|Weights by importance (rare & frequent)|Still doesn’t capture context or word order|
|**Word2Vec / GloVe**|Uses vector semantics (word meaning)|More complex, needs lots of data|
|**BERT**|Deep context-aware embeddings|Advanced and heavy computation|

---

## 📌 Summary (For Exam)

|Item|Notes|
|---|---|
|**TF-IDF**|Technique to weigh words by importance|
|**TF**|How often a word appears in a document|
|**IDF**|How rare the word is across documents|
|**Purpose**|Highlight meaningful terms, filter out common ones|
|**Used For**|Search, classification, filtering|
|**Better Than**|BoW, but simpler than embeddings like Word2Vec or BERT|

---

✅ **One-liner to remember:**

> TF-IDF highlights words that are **frequent in one document but rare in others**, making them good indicators of meaning.