**Multinomial Naive Bayes (Multinomial NB)** is a probabilistic classification algorithm mainly used for **text classification**. Think **spam detection, sentiment analysis, document categorization**, etc.

It belongs to the **Naive Bayes family**, which uses **Bayes' Theorem** plus a big simplifying assumption:  
all features are independent.

First, the core idea.

---

## 1. Bayes' Theorem (the backbone)

![[Pasted image 20260315185130.png]]

Where:

- **C** = class (spam / not spam)
    
- **X** = observed features (words in the document)
    

Meaning:

Posterior = Likelihood × Prior / Evidence

In practice we compute:

```
P(class | document)
```

for each class and pick the **largest**.

---

# 2. What makes it _Multinomial_

The **multinomial model** assumes features are **word counts**.

Example document:

```
"I love machine learning and learning ML"
```

Bag of words representation:

|word|count|
|---|---|
|love|1|
|machine|1|
|learning|2|
|ML|1|

Multinomial NB models the **frequency distribution of words** inside each class.

So instead of asking:

> Does the word appear?

It asks:

> **How many times does it appear?**

This matters a lot for text.

---

# 3. The probability model

For a document with words:

```
x1, x2, x3 ... xn
```

Multinomial NB computes:


$P(C|x_1,x_2,...x_n) \propto P(C)\prod_i P(x_i|C)^{count(x_i)}$  

Interpretation:

```
Class probability =
prior probability of class
× probability of each word in that class
```

If **"buy", "cheap", "discount"** appear a lot in spam emails  
then

```
P("buy"|spam)
```

will be large.

So a new email containing these words → classified as spam.

---

# 4. Small example

Training data:

|doc|text|class|
|---|---|---|
|1|cheap pills buy now|spam|
|2|buy cheap medicine|spam|
|3|meeting tomorrow|ham|
|4|project meeting schedule|ham|

Now we calculate:

### Prior

```
P(spam) = 2/4
P(ham) = 2/4
```

---

### Word probabilities

Example for spam:

Words in spam docs:

```
cheap pills buy now buy cheap medicine
```

Counts:

|word|count|
|---|---|
|cheap|2|
|buy|2|
|pills|1|
|now|1|
|medicine|1|

Total words = **7**

So

```
P(cheap | spam) = 2/7
P(buy | spam) = 2/7
```

---

# 5. Classifying a new document

New email:

```
buy cheap pills
```

Compute:

```
P(spam | doc)
P(ham | doc)
```

Whichever is larger wins.

Spam will dominate because those words appeared frequently in spam training data.

---

# 6. Laplace Smoothing (very important)

Problem:

If a word never appeared in training data

```
P(word | class) = 0
```

Multiplying by zero → entire probability becomes **zero**.

Fix: **Add-one smoothing**

[  
P(word|C) = \frac{count(word,C) + 1}{total_words_C + V}  
]

where **V = vocabulary size**

This prevents zero probabilities.

---

# 7. Why it works ridiculously well for text

Even though the independence assumption is **totally false**, it works because:

- Text has **high dimensional sparse features**
    
- Word frequencies are informative
    
- Fast training
    
- Very small data needed
    

That’s why **spam filters used it for years**.

---

# 8. When to use Multinomial NB

Great for:

- document classification
    
- spam detection
    
- sentiment analysis
    
- topic classification
    

Not great for:

- continuous numeric data
    
- complex feature interactions
    

---

# 9. In Python (scikit-learn)

Example:

```python
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

docs = [
    "cheap pills buy now",
    "buy cheap medicine",
    "meeting tomorrow",
    "project meeting schedule"
]

labels = ["spam","spam","ham","ham"]

vectorizer = CountVectorizer()
X = vectorizer.fit_transform(docs)

model = MultinomialNB()
model.fit(X, labels)

test = vectorizer.transform(["buy cheap pills"])
print(model.predict(test))
```

---

# One cool thing you might like

Since you're diving into **machine learning and simulations**, Multinomial NB is a perfect **first model to implement from scratch**.

It’s basically:

```
count words
compute probabilities
multiply probabilities
argmax
```

Super clean mathematically.

---

If you want, I can also show you something **very cool**:

**How to implement Multinomial Naive Bayes from scratch in ~30 lines of Python** (no sklearn).

It’s one of those algorithms where after coding it once, the whole ML pipeline suddenly makes more sense.