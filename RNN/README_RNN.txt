1.RNN Model Architecture



•	Input Shape: 

the model is designed to process sequences of embeddings, where each sequence corresponds to a series of word embeddings in a tweet, for instance.


•	Masking Layer: 

The Masking layer is used to handle variable-length sequences, which is common in NLP tasks.
It sets a mask value (e.g., 0.0) for padding tokens that do not carry meaningful information.
This ensures that the padded tokens do not contribute to the model's learning, as they are ignored during processing.


•	First SimpleRNN Layer:

The first SimpleRNN layer is a traditional RNN layer:
It processes the input sequence one time step at a time (as per the RNN's rule of sequential processing).
The parameter return_sequences=True is important because it ensures that the output at each time step is passed to the next layer in the network. This is necessary when you want to feed the RNN output to another RNN layer. The output from this layer is a sequence (of the same length as the input sequence), which is passed along to the next RNN layer.
Dropout is applied to help prevent overfitting by randomly setting some fraction of the output units to zero during training.


•	Second SimpleRNN Layer:

The second SimpleRNN layer processes the sequence of outputs from the previous RNN layer.
return_sequences=False (which is the default), this layer only returns the final output (the last time step of the sequence) to pass to the next layer. This is typical when you want to perform a classification task and only care about the final output after processing the entire sequence.
Dropout is applied again to prevent overfitting.


•	Dense Layer:

A Dense layer with 64 units and a ReLU activation function is added:
The Dense layer allows the model to learn higher-level representations after the sequential data has been processed by the RNN layers.
ReLU activation introduces non-linearity, which allows the model to learn more complex patterns.

•	Output Layer:

The final Dense layer has 3 units and uses a Softmax activation function:
The output layer has 3 units because the task is a multi-class classification problem (e.g., classifying tweets into 3 categories: toxic, offensive, and neutral).
Softmax activation is used to output a probability distribution across the 3 classes. The model will output the probabilities for each class, and the class with the highest probability is chosen as the prediction.




2.Techniques Applied



•	EarlyStopping: To avoid overfitting, the training process stops early if the validation loss does not improve for a specified number of epochs.

•	Class Weighting: The model incorporates **class weights** to handle imbalanced classes, ensuring that the model doesn’t become biased toward the majority class.

•	Evaluation Metrics: The model’s performance is evaluated using multiple metrics:  Accuracy, Precision, Recall, and F1-Score. These metrics provide a comprehensive view of how well the model is detecting toxic speech.

•	Dropout: Dropout layers are used to prevent overfitting by randomly setting a fraction of input units to 0 at each update during training.

•	ReLU Activation: ReLU (Rectified Linear Unit) is used in the hidden layers for introducing non-linearity, helping the model capture complex patterns in the data.

•	Softmax Output: Softmax is applied to the output layer, which is common for multi-class classification problems, as it converts the raw output values into probabilities.

•	Adam Optimizer: Adam is chosen for its adaptive learning rate, making it a good choice for training deep neural networks.

•	Categorical Cross-Entropy Loss: This is the appropriate loss function for multi-class classification problems, where the model outputs probabilities for each class.

•	Hyperparameter Tuning: The hyperparameters were manually tuned by experimenting with different configurations of the model.

