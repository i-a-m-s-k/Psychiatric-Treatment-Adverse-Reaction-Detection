# Named Entity Extraction (NER)
### TASK DESCRIPTION

This overall goal of the assignment is to work on the task with an approach for named entity recognition.
The material for the task is provided here: a) data files Download data files, sample code for b) CRF Download CRF 
and c) LSTM( colab link: https://bit.ly/lhs712w23_mar13Links to an external site.). 

### Dataset Description:
You have been provided a dataset of psychiatric treatment adverse reactions. This dataset contains patients’ expression of effectiveness and adverse drug events 
associated with four psychiatric medications -- Zoloft, Lexapro, Cymbalta, and Effexor XR. Each review is split into sentences, and all sentences are included in
the dataset -- not just those that contain an entity of interest. There are two entities of interest -- AE (adverse events) and SSI (signs, symptoms, and indications). 
These are tagged in the dataset following the BIO scheme: B- to denote beginning of a tagged named entity, I- to denote inside a tagged named entity tag, and O to denote
outside of any tagged named entity. So, your sequential labeling task has five tags: B-AE, I-AE, B-SSI, I-SSI, and O.

You have been provided with a training file that contains 4,744 sentences coming from 711 reviews. The test file has 1,259 sentences from 180 reviews. 
The training and test sentences are provided in the _TEXT files that have two tab-separated columns -- ID and SENTENCE.
•	ID is a unique string per review sentence and encodes within it the drug name, review number, and sentence number within the review.
•	SENTENCE is a sentence from the text review, with space separating the tokens in the sentence.
The labels for the train set are provided in one of two formats. The _LABELSEQ file has two tab-separated columns -- ID and TAGSEQ
•	ID is the same unique string as in .TEXT file 
•	TAGSEQ is a sequence of space-separated named-entity tags, one for each token in the sentence. The number of token matches the space-separated text in the .TEXT file
An alternate format for the labels is provided in the _LABELSTR file. This file lists each entity of interest found in the sentence in a line of its own. 
The _LABELSTR file has three tab-separated columns -- ID, TAG, and ENTITYSTR
•	ID is the same unique string as in .TEXT file 
•	TAG is one of two tags of interest, AE or SSI.
•	ENTITYSTR is the entity string text 
As you will notice, the number of lines in _LABELSTR file is different from that in _TEXT file because some sentences may have more than one entities
(so will need multiple lines), while others may have no entities and will not appear in the _LABELSTR file.  The number of lines in the _LABELSEQ file matches 
those in the _TEXT file.

### To - Do:
CRF and Deep Learning models
Task: Train a machine learning model using the provided training dataset to identify adverse events and SSI from drug reviews. 
You are provided with sample code in Python to read in the training data in _LABELSEQ format, and train a CRF model Download CRF modeland a Bi-LSTM model 
( colab link:  https://bit.ly/lhs712w23_mar13Links to an external site.) . You will:
A.	Add features to the CRF model to further improve the performance from the baseline model provided. You will describe the sets of features you added and how
these improved the performance in your report.
B.	Change the LSTM model, by changing its configuration, adding layers, changing the embedding, etc. to further improve the performance from the baseline model provided. 
You will describe the model changes you made and how these improved the performance in your report.
C.	Choose one model and generate the labels in the _LABELSEQ file format for the test set and submit the file along with your report.

