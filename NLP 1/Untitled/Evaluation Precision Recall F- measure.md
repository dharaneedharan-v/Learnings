
## 🎯 Goal: Understand Precision, Recall, and F1 with a Simple Example

---

### 🧪 Situation:

You built a model to detect if a **review is positive**.  
You tested it on just **5 reviews**.

Here’s what happened:

|Review|Actual Label|Predicted by Model|
|---|---|---|
|1|Positive ✅|Positive ✅|
|2|Positive ✅|Negative ❌|
|3|Negative ❌|Positive ❌|
|4|Negative ❌|Negative ✅|
|5|Positive ✅|Positive ✅|

---

### 📊 Now Count:

Let’s find:

- ✅ **True Positives (TP)** = model said "positive", and it was actually positive → Review 1 and 5 → **TP = 2**
    
- ❌ **False Positives (FP)** = model said "positive", but it was actually negative → Review 3 → **FP = 1**
    
- ❌ **False Negatives (FN)** = model said "negative", but it was actually positive → Review 2 → **FN = 1**
    

---

### ✅ Now Calculate:

#### **1. Precision**

**Formula:**

$$
Precision=TPTP+FP\text{Precision} = \frac{TP}{TP + FP}Precision=TP+FPTP​ Precision=22+1=23≈0.67\text{Precision} = \frac{2}{2 + 1} = \frac{2}{3} \approx 0.67Precision=2+12​=32​≈0.67
$$

> 👉 Out of all reviews predicted as **positive**, only **67%** were actually positive.

---

#### **2. Recall**

**Formula:**
$$

Recall=TPTP+FN\text{Recall} = \frac{TP}{TP + FN}Recall=TP+FNTP​ 

$$
$$
Recall=22+1=23≈0.67\text{Recall} = \frac{2}{2 + 1} = \frac{2}{3} \approx 0.67Recall=2+12​=32​≈0.67
$$

> 👉 Out of all **real** positive reviews, your model caught **67%**.

---

#### **3. F1-Score**

**Formula:**

$$
F1=2⋅Precision⋅RecallPrecision+RecallF1 = \frac{2 \cdot \text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}F1=Precision+Recall2⋅Precision⋅Recall​ F1=2⋅0.67⋅0.670.67+0.67=0.891.34≈0.66F1 = \frac{2 \cdot 0.67 \cdot 0.67}{0.67 + 0.67} = \frac{0.89}{1.34} \approx 0.66F1=0.67+0.672⋅0.67⋅0.67​=1.340.89​≈0.66
$$
---

### 🎉 Final Result (You can memorize this!):

|Metric|Value|Easy Meaning|
|---|---|---|
|Precision|0.67|Out of predicted positives, 67% correct|
|Recall|0.67|Found 67% of all actual positives|
|F1 Score|0.66|Balanced score between both|

