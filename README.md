# CNN Text Classification

**Run Instructions:**

There is a Jupyter notebook file. I was running the code in the following google colab environment
[link: https://colab.research.google.com/drive/1vKOWSqgIUnOUDnGn54L7I8hEpZzRpk_I?usp=sharing]. The code reads the data into a pandas DataFrame from my google drive. Any other
way of creating the DataFrame will also work. Each cell can be run step by step and will output the
results and figures in this document.


**Steps completed:**

The code implements a naive bayes classifier in step 1 with TF, TF-IDF for emeddedings in step 2, GLoVe vector embeddedings CNN network in step 3, 4 with various visualisations. In step 5 we try various improvements to the network. These improvements are detailed below.


**Improvements in step 5:**

I experimented with changing the CNN network architecture by adding more and different layers.

In particular, an additional convolutional layer was added, with both a larger filter and kernel size.
These have the effect of searching for larger and diferent patterns in the text. We hope that by
using the two convolutional layers, the network will generalise better.

After each convolutional layer, a batch normalisation layer was added, followed by a dropout layer
of 0.3, which effectively has the effect of feature selection.

The network is finished in the same way with a 1D global pooling layer and a ReLU activation
function layer, and finally a softmax function to get the final classification.

Additional experiments included- allowing the Glove embeddings to be trainable, allowing possible
optimisations and a reduced batch size.


**Results:**

Step 1:

The classifier performs quite well even in the most simple case of a naïve bayes model trained
with TF.

Step 2:

The classifier performs very similarly when using TF-IDF.


Step 3:

The performance is not notably better but still good. We can see the model is overfitting with 10
epochs, with validation loss increasing after epoch 6. The training data accuracy increases
significantly from epoch 3 to epoch 10, but the validation accuracy remains roughly the same at
about 90%.


Step 4:

The performance in the Glove embeddings classifier is actually worse after 10 epochs. However,
we note that the both the training and test accuracy were continuing to improve, and validation
loss for both were continuing to decline. This suggests that the model was still improving in a way
which generalised well to the test data. It is likely that this model would continue to show further
improvements with more epochs.



Step 5:

We can see from about epoch 4 that the model is starting to overfit with the validation loss
increasing every epoch from 5. The training accuracy continued to improve and loss drop, but did
not generalise as well. The model still performs well though, achieving and accuracy of 91% or 92%
if stopped at epoch 4.