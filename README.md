# Project-BTech-Final-Year
**Creating Browser Extension for Toxic Comment Detection and Blocking**

**Overview**

Introduction
Problem Statement
Objective
Dataset Collection
Data Preprocessing
Modelling
User Interface for extension
Conclusion


**Introduction**
The increasing amount of time people spend online is increasing day by day. 
As a result it becomes imperative to introduce systems that can detect Toxic and Hateful commentary online.
In this project we try to build such system in the form of browser extension by which we can detect toxic and hateful comments and totally prevent such pages from opening.
 


**Problem Statement**
Making a browser extension that detects 
and blocks Web pages with toxic and hateful comments.

**Objective**
Try to investigate various machine learning models that can identify Toxic comments appearing online.
Building the browser extension using the best performing model.
Detecting toxic comments and block the web pages
Modifying the browser extension to block Youtube videos by analysing the toxicity of its comment section.

**Dataset Collection**
Background - When the Civil Comments platform shut down,they made their 2 million public comments from their platform available online so that researchers could understand and improve civility in online conversations.

The dataset is thus collected from the Civil Comments platform. 


Jigsaw AI then sponsored the effort to collect and product the dataset
Add skewness to pre processing
Number of examples


In the dataset the text of the comment is found in the (comment_text) column. 
Also each comment in the train data has a toxicity label (target) which lies between 0 to 1. 
The (target) attribute is a fractional value which represents the fraction of human raters who believed the particular attribute(eg insult,threat,obscene) applied to the given comment.
We are taking the measure of target_toxicity as 0.7 
Thus if the target_toxicity > 0.7 then we classify the comment as toxic else it is not.


In this image we are showing the first 5 rows of the dataset

Explanation of the previously shown dataset
Python command ‘train.head(5)’ prints the first 5 rows of the dataset.
id shows the row number of the data (data is randomly arranged)
target denotes the target toxicity of the comment as rated by people.
comment_text is the actual comment being analysed.
severe_toxicity, obscene, identity_attack, threat are the attributes on which people rated the comment.
funny, wow, sad, likes,disagree are the reactions given to the comment on the platform.


**Data Preprocessing**
The following preprocessing are applied to comment data :-
Drop rows where target has a null value.


- Here the number of null values is 0



Drop unrelated columns(id, time of creation etc.)

- Selecting only the required columns

Convert all comments to lowercase and replace punctuation with white space.


Remove non-ascii characters and replace ‘\n’ with space .



**Class Imbalance Handling**

By counting the targets >=0.7 as toxic and <0.7 as non toxic we get the following table which shows that the dataset is highly skewed.



To address the imbalance between the non toxic and toxic data, the toxic dataset is oversampled.
Toxic 2.51%
Not Toxic 97.48%

**Modelling**
First TF-IDF is used to transform a text comments into fixed length vector representations
The transformed dataset is split into train and test dataset
Various classifiers are trained on the training set and then tested on the test set
F1-Scores for the classifiers is preferred over accuracy as a metric


Read TFIDF
Read F1 score
Add a slide related to metrics

Modelling-Logistic Regression
Logistic Regression serves as a good baseline for evaluating classification tasks
It tries to find a linear decision boundary which separated the dataset into different classes


Read TFIDF
Read F1 score
Add a slide related to metrics
Sensitivity/recall – how good a test is at detecting the positives. A test can cheat and maximize this by always returning “positive”.
Specificity – how good a test is at avoiding false alarms. A test can cheat and maximize this by always returning “negative”.
Precision – how many of the positively classified were relevant. A test can cheat and maximize this by only returning positive on one result it’s most confident in.
A macro-average will compute the metric independently for each class and then take the average (hence treating all classes equally)



Modelling-Logistic Regression
Logistic Regression despite being a simple baseline performs well for classification

Modelling-KNN
KNN or K-Nearest Neighbours algorithm tries to classify data points based on the labels of its k-nearest neighbours.

Modelling-KNN
KNN struggles to find classify the data points 
F1 score for Toxic comment(=1) is very low

Modelling-SVM
SVM or Support Vector Machines transforms non-linearly separable data points to higher dimensions
This helps the SVM to easily find decision boundaries 

Modelling-SVM
SVM generalizes well on this dataset for both positive and negative examples

Modelling-Random Forest
RF operate by constructing a multiple decision trees at training time. 
For classification tasks, the output of the random forest is the class selected by most trees. 

Modelling-Random Forest
RF are hard to train but seem to be struggling on positive toxic comment case

Conclusion
A relatively simple classifier like Logistic Regression outperforms other heavy classifiers such as KNN and RF.
SVM overall gives the best performance compared to other classifiers .
Thus for building the browser extension we will consider logistic regression due to its light weighted  and pretty close performance with respect to SVM. 

THANK YOU

Amar Lal Singh(18JE0093)

Anant Dev(18JE0102)
