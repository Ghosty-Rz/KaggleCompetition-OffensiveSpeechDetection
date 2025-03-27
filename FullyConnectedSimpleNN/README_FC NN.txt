1.Fully connected feedforward neural network Architecture:

This model is a  feedforward neural network with dense layers, which may still be effective for tasks like classification but does not utilize the sequential information that a traditional RNN or LSTM would capture.
The architecture is as follows:


•	Input Layer:
The input consists of tokenized tweet data. The tweets are first converted into numerical representations using word embeddings, specifically Word2Vec embeddings.

•	First Dense Layer:
The first layer is a Dense layer with 256 units and a ReLU activation function. This layer transforms the input embeddings into a higher-dimensional representation.
Dropout is applied after this layer with a dropout rate of 0.5 to prevent overfitting.

•	Second Dense Layer:
The second layer is another Dense layer with 128 units and a ReLU activation function. It further refines the model’s learned representation.
A Dropout rate of 0.5 is again applied.

•	Third Dense Layer:
This layer has 64 units and uses ReLU activation, allowing the model to capture more complex features before the final classification.

•	Output Layer:
The final layer has 3 units, corresponding to the three classes: toxic, offensive, and neutral.This layer uses the Softmax activation function to output the probabilities of each class.

  


2.	Techniques Applied


•	EarlyStopping: To avoid overfitting, the training process stops early if the validation loss does not improve for a specified number of epochs.

•	Class Weighting: The model incorporates **class weights** to handle imbalanced classes, ensuring that the model doesn’t become biased toward the majority class.

•	Evaluation Metrics: The model’s performance is evaluated using multiple metrics:  Accuracy, Precision, Recall, and F1-Score. These metrics provide a comprehensive view of how well the model is detecting toxic speech.

•	Dropout: Dropout layers are used to prevent overfitting by randomly setting a fraction of input units to 0 at each update during training.

•	ReLU Activation: ReLU (Rectified Linear Unit) is used in the hidden layers for introducing non-linearity, helping the model capture complex patterns in the data.

•	Softmax Output: Softmax is applied to the output layer, which is common for multi-class classification problems, as it converts the raw output values into probabilities.

•	Adam Optimizer: Adam is chosen for its adaptive learning rate, making it a good choice for training deep neural networks.

•	Categorical Cross-Entropy Loss: This is the appropriate loss function for multi-class classification problems, where the model outputs probabilities for each class.

•	Hyperparameter Tuning: The hyperparameters were manually tuned by experimenting with different configurations of the model.
