# Encoding and Embedding

## 1) One-Hot Encoding

**Question:** “Is the word present or not?”

- One-hot encoding uses a binary representation.
- If the word is present, it is marked as `1`; otherwise `0`.
- This is a simple and direct way to represent the presence of a word in a document.

Example vocabulary:

- `people`, `watch`, `like`, `movie`, `cricket`

Document vectors:

| Document | people | watch | like | movie | cricket |
| --- | ---: | ---: | ---: | ---: | ---: |
| D1 | 1 | 1 | 0 | 1 | 0 |
| D2 | 1 | 1 | 0 | 0 | 1 |
| D3 | 1 | 0 | 1 | 1 | 0 |
| D4 | 1 | 0 | 1 | 0 | 1 |

This is a presence-based representation. It tells us whether a word exists, but not how often it occurs.

---

## 2) Bag of Words (BoW)

**Question:** “How many times does the word appear?”

- Bag of Words counts word frequencies in a document.
- It tracks the number of times each word appears, not just whether it appears.
- If a word repeats more in the same sentence, BoW assumes it is more important.

Example vocabulary:

- `again`, `and`, `cricket`, `like`, `lot`, `movie`, `people`, `watch`

Document vectors:

| Document | again | and | cricket | like | lot | movie | people | watch |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| D1 | 1 | 1 | 0 | 0 | 0 | 2 | 1 | 2 |
| D2 | 0 | 1 | 2 | 0 | 0 | 0 | 1 | 2 |
| D3 | 0 | 1 | 0 | 2 | 1 | 2 | 1 | 0 |
| D4 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 |

### Why BoW matters

- It is simple and easy to understand.
- It gives a numerical representation for text.
- It can be used as input for machine learning models.

### Pros of BoW

- Easy to implement
- Simple representation
- No training required
- Direct mapping from words to numbers

### Cons of BoW

- Sparse representation
- High dimensionality
- Vocabulary size grows quickly
- Memory wastage
- Fails to capture semantic meaning and context
- Cannot handle new words well (out-of-vocabulary issue)

> The vocabulary size can be very large, such as 10,000 words, and thus the vector dimension becomes huge.

---

## 3) TF-IDF

**Question:** “How important is the word in this document?”

- TF-IDF = Term Frequency × Inverse Document Frequency
- It gives more weight to words that are important in a specific document but less common overall.
- This reduces the weight of common words like “the” or “and” and increases the importance of rarer, more informative words.

Interpretation:

- Frequent words are not always meaningful.
- Rare but meaningful words can carry more information.

This helps when some words appear often in the corpus but are not very informative for the current document.

---

## 4) Embeddings

**Question:** “What is the meaning of the text in context (word, sentence, paragraph, corpus)?”

- Embeddings capture semantic and contextual understanding.
- They map words or text into dense vector spaces.
- Similar words or texts are placed closer together in vector space.

Examples:

- `Word2Vec`
- `Transformer-based models`

Embeddings are better than one-hot or BoW because they try to represent meaning, not just counts or presence.

---

## 5) Document-Level Representation

A document can be represented as a vector of the entire document.

Example documents:

- D1 → people watch movie
- D2 → people watch cricket
- D3 → people like movie
- D4 → people like cricket

A simple document vector may look like:

- D1 → `[1, 1, 0, 1, 0]`
- D2 → `[1, 1, 0, 0, 1]`
- D3 → `[1, 0, 1, 1, 0]`
- D4 → `[1, 0, 1, 0, 1]`

Here, the dimension of the vector depends on the size of the vocabulary.

---

## 6) Word-Level (Sequence) Representation

Each word can also be represented as a vector in a vocabulary space.

Example vocabulary:

- `people`, `watch`, `like`, `movie`, `cricket`

Then a word-level representation could be something like:

- D1 → people watch movie
  - `[1, 0, 0, 0]`
  - `[0, 1, 0, 0]`
  - `[0, 0, 0, 1]`

- D2 → people watch cricket
  - `[1, 0, 0, 0]`
  - `[0, 1, 0, 0]`
  - `[0, 0, 0, 1]`

This representation captures word order and sequence structure, but it still may be sparse and high-dimensional.

---

## 7) Vocabulary and Vector Dimension

The size of the vocabulary determines the vector dimension.

If the vocabulary is:

- `people`, `watch`, `like`, `movie`, `cricket`

then the feature vector dimension is `5`.

In general:

- `dimension = number of unique words in the vocabulary`

This means:

- more unique words → larger vector size
- larger vocabulary → higher-dimensional representation

This is one reason high-dimensional representation can become difficult to manage.

---

## 8) Sparse vs Dense Representation

### Sparse representation

- Most values are zero
- Large memory usage
- Hard to scale with large vocabularies
- Difficult for many machine learning systems

### Dense representation

- Smaller vectors with meaningful values
- Better at capturing similarity and semantics
- Common in modern deep learning and NLP

Examples of dense models:

- `Word2Vec`
- `RNN`
- `LSTM`
- `GRU`
- `Transformer`
- `Attention-based models`

Dense embeddings are preferred because they hold more useful information than sparse count vectors.

---

## 9) Data, Numbers, Features, and Models

The handwritten notes show the pipeline:

- Data
- Numbers
- Features
- Model
- Prediction / output

This means:

- raw text is transformed into numbers
- numbers become features
- features feed into a model
- the model learns patterns and makes predictions

A common flow is:

- text → preprocessing → tokenization → feature extraction → model → prediction

---

## 10) Embeddings and Meaning

The key idea is that meaning is not just stored as words or counts. It is stored in relationships between words and contexts.

Examples from notes:

- one-hot and BoW are basic representations
- TF-IDF gives importance weighting
- embeddings give semantic and contextual meaning
- transformer-based models understand meaning in context

This is why modern NLP focuses on embeddings and pretrained language models.

---

## 11) Real-World ML/DL View

The notes also connect this topic to modern AI systems:

- `ML` = Machine Learning
- `DL` = Deep Learning
- `RNN` = Recurrent Neural Network
- `LSTM` = Long Short-Term Memory
- `GRU` = Gated Recurrent Unit
- `Attention` = focuses on relevant parts of input

These models can use embeddings as input and learn context from text sequences.

---

## 12) Quick Revision Summary

### One-hot encoding

- word present or not
- binary values
- simple but sparse

### Bag of Words

- counts repeated words
- more frequent words have more weight
- sparse and high dimensional

### TF-IDF

- counts + importance weighting
- reduces common-word impact
- emphasizes informative words

### Embeddings

- capture semantic meaning
- learn from context
- used in modern NLP and deep learning

### Final idea

- One-hot and BoW are basic text representations.
- TF-IDF adds importance weighting.
- Embeddings are the modern representation of meaning.
- Dense vectors are essential in machine learning and deep learning models.

---

## 13) Final Notes from the Handwritten Pages

- Vocabulary size can be very large, e.g. 10,000 words.
- High dimensionality increases vector size.
- Sparse matrices waste memory.
- Dense embeddings are more efficient and expressive.
- Modern systems learn meaning from context rather than just word counts.
- Data → numbers → features → model → output is the core flow in NLP and ML.

This is the complete conceptual view of encoding and embedding as written in the handwritten notes.
