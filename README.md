[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/ymop5HUw)
# CMPSC 310 Activity 15

## Deadline: April 12 by 9:50am

## Assignment

 For this activity follow [Neural machine translation with a Transformer and Keras](https://www.tensorflow.org/text/tutorials/transformer).

## Submission

### dataset and preprocessing

In this project, the author used the dataset, Portuguese-English dataset. This dataset contains approximately 52,000 training, 1,200 validation and 1,800 test examples.

After the dataset is imported and examples are fetched. Those raw sentence data is transformed into encoded token IDs by tensorflow tokenizer model. Then token IDs should be detokenized into human readable sentences again. Within this process, punctuations are deleted and all words are lowercased. Some words are split into sub words like searchability is broke into search and ability

The tf.saved_model contains two text tokenizers, one for English and one for Portuguese. Both have the same methods.
Input will be split into values and label where label will be the id of the next token.

RaggeredTensor will be converted into Tensors

The resulting tf.data.Dataset objects are setup for training with Keras. Keras Model.fit training expects (inputs, labels) pairs. The inputs are pairs of tokenized Portuguese and English sequences, (pt, en). The labels are the same English sequences shifted by 1. This shift is so that at each location input en sequence, the label in the next token.

### Transformer breakdown

During the process of converting Portuguese into English, transformer model will accept numeric data which could be understood by computers. So before all other processing, we need a layer of code to convert those texts into vectors (numbers). Then to make transformer model to notice the matter of order, we add something called positional encoding

Then a ADD and Norm step will ensure the value of vectors will be updated. It provides a direct path for gradient.

Finally attention layer will be added to consult the whole context of a token.