📘 Assignment 1: Sanskrit–English Cross-Lingual Embedding Alignment
🔍 Overview

This assignment implements a cross-lingual sentence embedding system for Sanskrit–English parallel data. The goal is to map sentences from both languages into a shared semantic vector space, where aligned sentence pairs have high similarity.

Instead of generating translations, the system evaluates semantic alignment using embedding similarity and retrieval metrics.

The implementation uses the pre-trained LaBSE model.

🎯 Objectives
Generate language-agnostic embeddings for Sanskrit and English sentences
Evaluate alignment using cosine similarity
Perform retrieval-based evaluation (Precision@K)
Reduce embedding dimensionality using PCA
Visualize alignment using t-SNE
🏗️ Methodology
1. Data Preprocessing
Sanskrit normalization:
Unicode normalization (NFC)
Standardization of danda symbols
Whitespace cleanup
English normalization:
Quote normalization
Whitespace cleanup
Removed:
Null values
Empty sentences
2. Sentence Embeddings
Model: LaBSE
Output: 768-dimensional embeddings
Embeddings are L2-normalized

Used:

model.encode(..., normalize_embeddings=True)

3. Joint PCA with Whitening
Sanskrit and English embeddings are combined
PCA is applied jointly:
whiten = True
Shared projection space

Tested dimensions:

32, 64, 128, 256, 512, 768

Best trade-off: 64 dimensions

4. Evaluation Metrics
Cosine Similarity
Measures similarity between aligned pairs
Precision@K (Retrieval)
For each Sanskrit sentence:
Retrieve top-K English candidates
Check if correct pair is retrieved

Metrics used:

Precision@1
Precision@5

5. Visualization
t-SNE applied on 100 sampled sentence pairs
2D visualization of embeddings
Lines drawn between aligned pairs
📊 Results
High cosine similarity for aligned pairs
Strong retrieval performance (P@1, P@5)
Minimal loss after PCA reduction
Significant improvement in efficiency
t-SNE shows clear cross-lingual alignment
🧪 Experiments
PCA dimensionality sweep
Similarity retention after reduction
Retrieval evaluation across dimensions
Analysis of best and worst aligned pairs
📌 Key Insights
Pre-trained multilingual embeddings effectively capture semantics
Joint PCA preserves alignment across languages
Retrieval-based evaluation is more informative than similarity alone
⚠️ Limitations
No translation generation
No fine-tuning on dataset
Performance depends on pre-trained model
PCA is a linear transformation
🚀 Future Work
Fine-tuning on Sanskrit–English data
Contrastive learning approaches
Non-linear dimensionality reduction
Retrieval-based translation system

⚙️ Installation
pip install sentence-transformers scikit-learn numpy pandas matplotlib
▶️ Usage
jupyter notebook Assignment1_Sanskrit_Embeddings.ipynb

📚 References
LaBSE
SentenceTransformers
BERT (Devlin et al., 2018)
Sentence-BERT (Reimers & Gurevych, 2019)
Scikit-learn Documentation
📌 Pre-trained Model Disclosure
Model: LaBSE
Usage: Direct embedding extraction (no fine-tuning)
👤 Author

Shasank Dixit
