
## 📘 What is **Cosine Similarity**?

**Cosine Similarity** is a metric that measures **how similar two vectors are**, based on the **angle** between them — not their length.

---

### 🧠 Think of it like this:

- Words are represented as **vectors** (like `[0.2, 0.7, -0.1]`)
    
- **Cosine Similarity** checks the **direction** of those vectors  
    → If they point in the same direction, they are **similar**  
    → If they point in opposite directions, they are **dissimilar**
    

---

## 🎯 Why Use Cosine Similarity?

|Reason|Explanation|
|---|---|
|✅ **Scale-independent**|Only measures **angle**, not length — so text length doesn’t matter|
|✅ **Works with sparse data**|Great for comparing documents or word vectors|
|✅ **Efficient**|Fast to compute, even for large datasets|
|✅ **Intuitive results**|Value between **-1 (opposite)** and **1 (same)**|

---

## 🔧 Formula:

$$ {cosine\_similarity} = \frac{A \cdot B}{\|A\| \times \|B\|}$$​
$$
A⋅B =   dot product   of  the two vectors
$$
$$
∥A∥and ∥B∥ = magnitudes of each vector
 $$
    

---

## 💻 Example (Simple):

### Two word vectors:


```python
king = [1, 2] queen = [1.1, 2.1]
```

Compute cosine similarity:

- Angle between them = small
    
- Cosine similarity ≈ 0.999  
    → Very similar
    

---

## 📚 Applications in NLP:

|Use Case|Why Cosine Similarity?|
|---|---|
|**Document similarity**|Find how close two articles are|
|**Search engines**|Match queries with relevant results|
|**Word similarity**|Check closeness of meanings|
|**Recommendation systems**|Suggest similar items or content|
|**Plagiarism detection**|Compare documents for overlap|

---

## ⚠️ Limitations:

|Limitation|Why It Happens|
|---|---|
|No context|It only compares vector direction — doesn’t understand sentence meaning|
|Sensitive to data quality|Bad embeddings = bad similarity|
|Can’t detect antonyms|“good” and “bad” might look similar in some spaces|

---

✅ **One-liner**:

> Cosine Similarity tells how **similar two texts or words are**, based on **direction**, not size.