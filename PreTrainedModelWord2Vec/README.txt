Architecture and Techniques Applied

1. Word2Vec Embeddings:
Word2Vec is a pre-trained model that generates vector representations (embeddings) for words. These embeddings capture the semantic meaning of words, placing similar words closer together in a high-dimensional vector space.

By using pre-trained Word2Vec embeddings, we avoid training embeddings from scratch, leveraging the semantic relationships already learned from a large corpus of text.

The Word2Vec embeddings are used in the embedding layer of the model, where they are fixed (non-trainable) during training to retain their pre-trained knowledge.

2. Recurrent Neural Network (RNN) with LSTM:
LSTM (Long Short-Term Memory) cells are used to capture the temporal (sequential) dependencies in text data. Tweets are processed word by word, and LSTM cells help learn context over time.

The model uses a Bidirectional LSTM, which processes the input sequence in both forward and backward directions, providing richer context for better understanding.

3. Global Max Pooling:
After processing the sequences with LSTM, the Global Max Pooling layer reduces the output sequence into a fixed-size vector by selecting the maximum value from each feature. This helps capture the most important features and reduces the dimensionality.

4. Fully Connected Layers:
A Dense layer with ReLU activation is used to learn complex patterns from the pooled features.

Dropout is applied after the Dense layer to prevent overfitting by randomly dropping 50% of the neurons during training.

5. Output Layer:
The final Dense layer uses softmax activation to output probabilities for each class (non-offensive, offensive, hate speech). The class with the highest probability is selected as the model's prediction.

6. Loss Function and Optimization:
Sparse categorical cross-entropy is used as the loss function, suitable for multi-class classification tasks where labels are integers.

Adam optimizer is used for efficient and adaptive learning during training.