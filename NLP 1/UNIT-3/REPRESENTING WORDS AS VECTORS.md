## 1. **One-Hot Encoding**

### 🔧 How it works:

- Each word is given a unique binary vector.
    
- Only **1** in its own spot, **0s** everywhere else.
    

### 🧪 Example:

Vocabulary: `["bank", "money", "river", "loan"]`

|Word|One-hot vector|
|---|---|
|bank|`[1, 0, 0, 0]`|
|money|`[0, 1, 0, 0]`|

🔴 **Problem**: It treats all words as **totally unrelated** — "bank" and "money" look as different as "bank" and "fish".

✅ **Good for**: Simple models  
❌ **Not smart**, ❌ **Not context-aware**

---

## 🧠 2. **TF-IDF (Term Frequency–Inverse Document Frequency)**

### 🔧 How it works:

- Weighs words based on how **common** they are in a document vs all documents.
    
- Common words (like "the", "is") get **low weight**, unique words get **high weight**.
    

### 🧪 Example:

Let’s say:

- Doc1: "I went to the river bank"
    
- Doc2: "I took a loan from the bank"
    

TF-IDF will give:

- `"bank"` → High score (appears in both)
    
- `"river"` → High in Doc1, low in Doc2
    
- `"loan"` → High in Doc2
    

TF-IDF converts each **document** into a **vector** of term weights.

✅ **Good for**: Document classification, keyword extraction  
✅ **Smart in frequency**, ❌ **Not context-aware**  
(Doesn’t know which “bank” you mean)

---

## 🧠 3. **Word2Vec**

### 🔧 How it works:

- Uses a neural network to learn **word meanings based on context**.
    
- If "bank" is near "money", it's likely about finance.
    
- If "bank" is near "river", it's likely geographic.
    

### 🧪 Example:

Sentence A: "I deposited money in the bank"  
Sentence B: "I sat on the river bank"

Word2Vec will learn **two different vector clusters**:

- `"bank"` near `"money"`, `"loan"`, `"ATM"` → 💰
    
- `"bank"` near `"river"`, `"water"`, `"flood"` → 🌊
    

But! Word2Vec gives **one vector per word**, so it **can’t handle both meanings at once**.

✅ **Smart in capturing meaning**  
❌ **Not fully context-aware** (same "bank" in all cases)

---

## 🧠 4. **GloVe (Global Vectors)**

### 🔧 How it works:

- Looks at how frequently words appear **together** across a large corpus.
    
- Learns relationships like:
    
    - **“King - man + woman = queen”**
        

### 🧪 Example:

"bank" appears often with "loan", "cash", and also with "river", "flood".

So GloVe gives "bank" a vector that kind of **blends both meanings**.

✅ **Smart in meaning**, ❌ **Not context-aware**

---

## 🧠 5. **FastText**

### 🔧 How it works:

- Breaks words into **character sub-parts** like:
    
    - `"bank"` → `["ba", "ban", "ank", "nk"]`
        
- Learns word meaning from **subwords**, not just whole words.
    

### 🧪 Example:

New word: `"banking"`

- Even if "banking" wasn’t in training data, FastText understands it from parts like `"bank"` + `"ing"`
    

✅ **Smart with rare words**  
❌ Still **not context-aware**

---

## 🧠 6. **BERT** (Contextual Embeddings)

### 🔧 How it works:

- Understands the **entire sentence** before assigning vectors.
    
- Gives different vectors for the **same word** in different sentences.
    

### 🧪 Example:

- Sentence A: `"She deposited money in the bank"`  
    → `"bank"` = 💰 meaning
    
- Sentence B: `"He walked along the river bank"`  
    → `"bank"` = 🌊 meaning
    

🧠 BERT will generate **two completely different vectors for "bank"** based on the sentence.

✅✅ **Very smart**, ✅✅ **Fully context-aware**

---

## ✅ FINAL SUMMARY TABLE (with examples):

|Method|"Bank" in Sentence A (Money) vs B (River)|Smart?|Context-Aware?|
|---|---|---|---|
|One-hot|Same vector in both|❌ No|❌ No|
|TF-IDF|Weighted by doc frequency|✅ Some|❌ No|
|Word2Vec|Learns from general context, same vector|✅ Yes|❌ No|
|GloVe|Blended meaning from co-occurrence|✅ Yes|❌ No|
|FastText|Breaks into subwords, but one meaning|✅ Yes|❌ No|
|BERT|Learns meaning from full sentence context|✅✅ Yes|✅✅ Yes|

---

## 🧠 Why This Matters in NLP:

When building:

- **Search engines**: you want to know if "bank" = money or river.
    
- **Chatbots**: they must understand what the user _means_.
    
- **Translation systems**: need correct meaning of words in sentence.
    

Only **contextual models like BERT** solve this fully. Earlier methods were simpler but can’t handle ambiguity.


## 🧠 What is Skip-gram?

Skip-gram is a technique used in **Word2Vec** to **learn word vectors (embeddings)** by predicting the **context words** around a **target word**.

---

### 🎯 Purpose:

> Teach the model:  
> “If you know the **center word**, what words are likely to appear near it?”

---

## 🧪 Example:

Let’s say your sentence is:

```python
The cat sat on the mat
```


You choose a **window size = 2** (means look 2 words to the left and right).

Now, for the **target word** `"sat"`, the context words are:

``

```python 
["cat", "on"]
```

### Skip-gram turns this into training pairs:

|Input (Target)|Output (Context Word)|
|---|---|
|sat|cat|
|sat|on|

This is how Skip-gram learns:

- It sees `"sat"` near `"cat"` and `"on"`, so it **adjusts the word vectors** to reflect that relationship.
    

---

### 🧠 What Is It Doing Internally?

It’s training a simple **neural network** where:

- The input is a **one-hot encoded word**
    
- The network tries to **predict nearby words**
    
- During training, the **hidden layer weights become the word vectors**
    

---

## 🔁 Skip-gram vs CBOW

|Feature|Skip-gram|CBOW (Continuous Bag of Words)|
|---|---|---|
|Predicts|Context from target word|Target word from context|
|Example|`"sat"` → `"cat", "on"`|`"cat", "on"` → `"sat"`|
|Good for|Rare words|Frequent words|
|Training time|Slower|Faster|

---

## ✅ Summary (Exam Notes)

|Term|Definition|
|---|---|
|**Skip-gram**|Word2Vec model that learns by predicting context words from a target word|
|**Goal**|Learn word vectors that capture meaning based on context|
|**Input**|A center word|
|**Output**|Nearby context words|
|**Example**|`"sat"` → `"cat"`, `"on"`|

---

✅ **One-liner to remember**:

> Skip-gram teaches the model to **predict surrounding words** from a **given word** to learn useful word vectors.