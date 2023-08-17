# MNIST Classification with TensorFlow

This script showcases a simple dense neural network built using TensorFlow to classify the MNIST dataset of handwritten digits.

## Requirements:

- Python 3
- TensorFlow 2.x

```
pip install --upgrade certifi
pip install tensorflow
```

## Model Architecture:

1. Input layer that flattens the 28x28 images into a single vector.
2. Fully connected (dense) layer with 128 neurons and ReLU activation.
3. Dropout layer with 20% dropout rate to prevent overfitting.
4. Output fully connected (dense) layer with 10 neurons (corresponding to the digits 0-9).

The output layer does not employ a softmax activation, meaning the model outputs logits.

## Dataset:

The script employs the MNIST dataset of handwritten digits. The dataset is automatically fetched using TensorFlow's built-in datasets module.

## Data Preprocessing:

- The pixel values are normalized to lie in the [0,1] range.

## Training:

- Optimizer: Adam
- Loss function: Sparse Categorical Crossentropy (with logits, since the output layer doesn't have softmax activation).
- Number of epochs: 5

## Usage:

Execute the script using the following command:

```
python mnist_tf.py
```

## Expected Output:

After training, the script will output training metrics for each epoch including the loss and accuracy. Once training is complete, it will evaluate the model on the test set and display the test loss and accuracy. For example:

```
1794/1875 [===========================>..] - ETA: 0s - loss: 0.0749 - accuracy: 0.91829/1875 [============================>.] - ETA: 0s - loss: 0.0748 - accuracy: 0.91864/1875 [============================>.] - ETA: 0s - loss: 0.0748 - accuracy: 0.91875/1875 [==============================] - 3s 2ms/step - loss: 0.0747 - accuracy: 0.9762
313/313 - 0s - loss: 0.0691 - accuracy: 0.9781 - 408ms/epoch - 1ms/step
```

This indicates that the model achieved an accuracy of approximately 97.62% on the training dataset and 97.81% on the MNIST test dataset.

## Notes:

- The script employs a simple feedforward neural network without convolutional layers. This kind of architecture can achieve decent accuracy on the MNIST dataset but might not be suitable for more complex image datasets.
- The SSL context modification at the beginning of the script (`ssl._create_default_https_context = ssl._create_unverified_context`) is used to bypass SSL certificate verification. This is helpful in some environments where fetching the MNIST dataset might encounter certificate issues. Note: This may not be required in all environments and can pose security risks, so it should be used cautiously.

## Customizations:

For further experimentation, one can adjust the model architecture, optimizer settings, or the number of epochs. Introducing convolutional layers or other regularization techniques may further enhance the model's performance.
