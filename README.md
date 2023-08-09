# Psychiatric Treatment Adverse Reaction Detection

This repository contains code and resources related to the development and implementation of machine learning models for identifying adverse reactions and signs, symptoms, and indications (SSIs) in psychiatric treatment reviews using Conditional Random Fields (CRF) and Bidirectional Long Short-Term Memory (Bi-LSTM) models.

### Project Overview
The goal of this project is to enhance the identification of adverse events and SSIs in psychiatric treatment reviews using advanced machine learning techniques. The primary models employed are CRF and Bi-LSTM, both of which are well-suited for sequence labeling tasks. The project involves feature engineering, model tuning, and encoding schemes to achieve accurate predictions.

### Prerequisites
Make sure you have the following libraries and tools installed:

NLTK
spaCy
scikit-learn
PyTorch
TensorFlow
CRFSuite
Pandas
NumPy
Jupyter Notebook
Git
SparkSQL

### Data
The dataset used in this project consists of psychiatric treatment reviews annotated with adverse events and SSIs. Due to privacy and ethical considerations, the dataset cannot be provided in this repository. However, you can use your own dataset or seek access to similar data for experimentation.

### Long Short-Term Memory (LSTM) Model
For training the LSTM model, I tried varying values of batch size, epochs, output dimensions, dropout rate, and activation. I used epochs of 16, 32, 20, and 50 and was unable to monitor the validation loss during training to avoid overfitting. My model as a result achieved an accuracy of 99% at multiple instances where I set the loss function to “binary_crossentropy”. Increasing the epochs did not make much difference to the accuracy of the model. I also tried to decrease the learning rate as I thought it would help improve the accuracy of the model, however, I observed that there was only a slight change in the accuracy by a few decimals. I also increased the output dimensions to 100 and 300 and increased the units to 50 but that resulted in overfitting with 98% accuracy of the LSTM model. I noticed that there was overfitting of the model when we changed the loss function from “categorical_crossentropy” to “binary_crossentropy” which was as expected as “categorical_crossentropy” is better suited in this case. For the activation function, I tried using “sigmoid” and “relu” parameters and noticed that there was a higher accuracy in case of sigmoid that resulted in overfitting of the model. Thus, I chose the activation function as “relu”. Finally, I after multiple trial and error situations, I decided to set the MAXLEN=50 instead of 160 which is the maximum length of each sentence after it has been preprocessed and padded with a padding token “PAD” to ensure that all sentences have the same length. The pad_sequences() function from Keras padded all the sentences to a length of 50 and this helped in achieving an improved accuracy of 96%. Although I was able to achieve an accuracy of 96% with the LSTM model, there seemed to be an error while exporting files after running the model on the test data as all the outputs had a label of “O” which I assume might be due to overfitting of the data or some error while exporting/running the model on test data. 

### Conditional Random Field (CRF) Model 
One of the first things that I tried with CRF model was that I ran GridSearchCV to select the best combination of hyperparameters for the model by exhaustively searching over a specified range of hyperparameter values such as c1, c2, max_iterations, and linesearch. The GridSearchCV output was not helpful and impressive in spite of the fact that it took almost two hours to run because it gave 87% accuracy with hyperparameter tuning. The output was using algorithm as lbfgs, setting all possible transitions as true, c1 to 0.1, c2 to 0.1 and max_iterations to 50. I added three binary features to wordtofeatures() function which indicate whether an entire word is uppercase or not, the word is a digit or not, and the word is capitalized or not. I tried these features by setting the CRF Model having algorithm as lbfgs, all possible transitions to true, c1 to 0.1, c2 to 0.1 and max_iterations to 50. This helped me achieve 89% accuracy of the model and I was able to export the dataset in the format of sentence ID followed by BIO encoded labels after running the model on the test data. I also had tried other features such as if the word contains alphabetic characters only, string features indicating the last four or five characters of the word, integer feature indicating the length of the word and boolean feature indicating whether the word consists of whitespace characters only. These additional features led to decrease in accuracy of the model which is why I did not use them in training my model.

### Results
After thorough feature engineering and hyperparameter tuning, the CRF model achieved an accuracy of 89% on the given dataset. This high accuracy indicates the model's effectiveness in identifying adverse events and SSIs in psychiatric treatment reviews.
