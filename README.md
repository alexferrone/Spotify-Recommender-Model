# Spotify-Recommender-Model

This project implements a sequential track recommendation model for Spotify, leveraging NLP-based features and advanced deep learning techniques.

# Overview

The goal was to develop a model that recommends tracks based on the context of existing playlists. Starting with a dataset of over six million tracks and one million playlists, we downsampled to 10% (~600K tracks) for computational feasibility.

# Key Details

Course: MSBA 503: Analytics Programming II

Dataset: Over six million tracks and one million playlists, downsampled to ~600K tracks for model training and testing.

# Data Preprocessing and Feature Engineering

Normalization: Applied normalization to numerical and text-based columns.

Feature Creation: Introduced a diversity score calculated as a weighted average of artist and album diversity.

SBERT Embeddings: Used Sentence-BERT (SBERT) to embed playlist names and evaluated their significance in the recommendation task.

Validation Processing: Ensured the validation data followed the same preprocessing steps as the training data (2.3% track overlap).

Model Development

# Word2Vec Embeddings

Approach: Modeled playlists as "sentences" and tracks as "words."

Configuration: Employed a skip-gram model with a window size of 5.

Optimization: Introduced negative sampling to improve convergence.

Performance: Achieved high binary accuracy (~0.96).

# Bert4Rec Model

Input Handling: Created a global track map and introduced padding tokens ([PAD], [UNK]) for sequence alignment.

Embedding: Used a preloaded TensorFlow BERT model to encode input sequences.

Feature Aggregation: Combined track embeddings with auxiliary features into an aggregated projection.

Regularization: Applied dropout layers and masked language modeling (MLM) for sequence prediction.

# Optimization:

Gradient clipping and logit clamping to stabilize training.

Learning rate scheduler for optimized convergence.

Achieved a final training loss of 0.0004.

# Challenges

Memory Limitations: Constrained by computational resources during model optimization.

Exploding Gradients: Debugged and resolved issues related to unstable training dynamics.

Shape Misalignment: Addressed issues with tensor alignment during embedding and model integration.

# Performance Insights

Strengths: Strong performance on short playlists.

Weaknesses: Weaker results on long playlists.

Metrics: Achieved decent Normalized Discounted Cumulative Gain (NDCG) but underperformed on R-Precision.

# Future Improvements

Cold-Start Problem: Develop logic to handle recommendations for new users and tracks.

Feature Expansion: Introduce additional features to enhance model performance.

Refine Sampling: Improve negative sampling techniques to better represent user preferences.
