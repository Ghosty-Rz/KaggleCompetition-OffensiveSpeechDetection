GRU Model:
This model is constructed based on a feedforward neural network architecture rather than a recurrent one.

1. Model Architecture
Our GRU model consists of the following layers:
 •Masking Layer: Handles variable-length sequences by ignoring timesteps where all features are 0.0.
 •First GRU Layer: Extracts sequential patterns from input embeddings. It contains units_1 GRU cells (default 256), outputs a sequence for the next GRU layer, and applied dropout regularization.
 •Second GRU Layer: It contains units-2 GRU cells (default 128), applies dropout regularization, and does not return sequences as it connects to a dense layer.
 •Dense Layer: A fully connected layer with 64 neurons that uses ReLu activation to learn complex features followed by Dropout to prevent overfitting.
 •Output Layer: A Dense layer with 3 units and a softmax activation function to output probability distributions across the three classes.

2. Techniques Applied
Several techniques were employed in this model:
  -Dropout Regularization: Dropout layers with a tuned dropout rate are added to mitigate overfitting by randomly disabling neurons during training.
  -Adam Optimizer: The Adam optimizer is used with a tuned learning rate, providing an adaptive learning rate for efficient training.


  -Categorical Cross-entropy Loss: The loss function used is categorical cross-entropy, which is standard for multi-class classification tasks.

