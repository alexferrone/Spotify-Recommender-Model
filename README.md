# Spotify-Recommender-Model
Executive Summary: Spotify Recommender Model
Course: MSBA 503: Analytics Programming II
Objective:
Develop a sequential track recommendation model using a limited set of NLP-based features. The dataset included over six million tracks and a million playlists, which we downsampled to 10% (~600K tracks) for manageability.
Data Preprocessing and Feature Engineering:
Normalized numerical and text-based columns. Created additional features like a diversity score (weighted average based on artist/album diversity). Used SBERT to embed playlist names, testing their significance. Processed validation data similarly to training data (2.3% track overlap).
Model Development:
Word2Vec Embeddings:
Treated playlists as “sentences” and tracks as “words.” Used a skip-gram model with an optimal window size of five. Introduced negative sampling for enhanced convergence. Achieved high binary accuracy (~0.96).
Bert4Rec Model:
Created a global track map and introduced padding tokens ([PAD], [UNK]) for sequence alignment. Used a preloaded TensorFlow Bert model to encode input sequences. Combined track embeddings and auxiliary features into an aggregated projection. Regularization through dropout layers and masked language modeling (MLM) for sequence prediction. Applied gradient clipping and logit clamping to stabilize training. Implemented a learning rate scheduler for optimized training (final loss: 0.0004).
Challenges:
Memory limitations due to model optimization.
Debugging exploding gradients.
Addressing shape misalignment issues.
Performance Insights:
Strong performance on short playlists; weaker performance on long playlists.
Decent NCDG score but poor R-precision score.
Future Improvements:
Develop cold-start logic for new users/tracks.
Introduce additional features and refine negative sampling.

