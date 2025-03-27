1. Model Architecture
. Input Layer: The input shape for the model is (batch_size, max_sequence_length,embedding_dim), where:
   batch_size: Number of samples per batch.
   max_sequence_length: Maximum length of the input sequences.
   embedding_dim: Dimension of each word embedding.

. Reshape Layer: Reshapes the input data to ensure it is compatible with the 1D convolutional layers.
Output Shape: (batch_size, max_sequence_length, embedding_dim).

. Convolutional Layers (1D): For feature extraction from n-grams
 . Conv1D Layer (3-gram patterns): Filters (128), kernel size = 3. Captures local n-gram patterns in the text (e.g., 3 consecutive words).
 . Conv1D Layer (4-gram patterns): Filters (128), kernel size = 4.Captures different local patterns of 4 consecutive words.
 . Conv1D Layer (5-gram patterns): Filters (128), kernel size = 5.Captures 5 consecutive word patterns.

. TimeDistributed Layer: Ensures that each convolution layer is applied to every timestep in the input sequence.
Output Shape: (batch_size, max_sequence_length, 128) for each convolution layer.

. Global Max Pooling Layer: Applies a global max pooling operation to select the most important feature from the entire sequence for each filter (from each convolution).
Output Shape: (batch_size, 128).

. Dense Layers:
  . First Dense Layer: 256 neurons, ReLU activation.
  . Second Dense Layer: 128 neurons, ReLU activation.
  . Third Dense Layer: 64 neurons, ReLU activation.
These layers learn complex patterns and perform feature transformation.

. Dropout Layers: Dropout is applied after the dense layers to reduce overfitting by randomly setting a fraction of the input units to 0 during training.
Dropout Rate: Controlled by the dropout_rate argument.

. Output Layer: Dense Layer (3 neurons): Uses a softmax activation function to output a probability distribution over 3 classes.
Output Shape: (batch_size, 3).

2. Techniques Applied
Several techniques were employed in this model:
  -Dropout Regularization: Dropout layers with a tuned dropout rate are added to mitigate overfitting by randomly disabling neurons during training.
  -Adam Optimizer: The Adam optimizer is used with a tuned learning rate, providing an adaptive learning rate for efficient training.

