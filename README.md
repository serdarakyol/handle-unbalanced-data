# Handling the unbalanced data
The dataset contain 284807 data. Extremely unbalanced dataset. Following steps applied

1. [Usage](#1-usage)
2. [Explore the dataset](#2-explore-the-dataset)
3. [Handle missing values](#3-handle-missing-values)
4. [Trained various models](#4-trained-various-models)
5. [Calculated custom accuracy](#5-calculated-custom-accuracy)
6. [Used ROC curve to detect best threshold](#6-used-roc-curve-to-detect-best-threshold)
7. [Trained K-means clustering with cosine distance metric](#7-trained-k-means-clustering-with-cosine-distance-metric)
8. [Evaluated class 1 based on K-means algorithm](#8-evaluated-class-1-based-on-k-means-algorithm)
9. [Conclusion](#9-conclusion)

# 1. Usage
I highly recommand that you use Virtual Env. Download and enter that repository direction on terminal. If you have not installed Jupyter Notebook you can install with ```pip install jupyterlab```. If you installed the Jupyter notebook follow description below
```
$ virtualenv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
$ jupyter-lab .
```
Now, you can enjoy from the notebook.

# 2. Explore the dataset
The dataset contains 284807 data. 284315 class_0 and 492 class_1

# 3. Handle missing values
Replaced null values with each column average. E.g: calculated average of p1 and replaced with null values in p1. Repeated the same process with other columns too.

# 4. Trained various models
Trained Logistic Regression, SVM, Random Forest Classifier, KNeighbors Classifier, Gaussian NB

# 5. Calculated custom accuracy
Penalised class_0 for calculate accuracy. If the model predicted class_1 correctly added (class_0/class_1) score else, added 1 to correct counter variable

# 6. Used ROC curve to detect best threshold
Plotted ROC curve to see which model can be more accurate and detect best threshold for each model

# 7. Trained K-means clustering with cosine distance metric
Normally K-Means algorithm comes with euclidian distance metric but monipulated the algorithm and chnged distance metric. Used cosine distance metric

# 8. Evaluated class 1 based on K-means algorithm
Visualised K-Means prediction and calculated accuracy based on class_1

# 9. Conclusion
MODEL(s)|  ACCURACY | MODEL SIZE | ACCURACY AFTER SET THRESHOLD
--- | --- | --- | ---
Logistic Regression | %16 | 984 bytes | %22
Gaussian NB | %21 | 1.2 kB | %27
SVM | %15 | 88,2 kB | %16
Random Forest Classifier | %20 | 4,8 MB | %29
KNeighbors Classifier | %19 | 49.9 MB | %21 
K-Means | %38 | - | -

## Random Forest
Pros: Highest accuracy for that case. 

Cons: Creates lot of three which means calculation will be too much. Also training period will be longer because of that too

## Logistic regression
Pros: Trains and predicts fast, can give good accuracy for simple dataset. There are regularization for techniques to avoid overfitting. Good for binary classification. Model size is really light 

Cons: Not accuracy for complex dataset. Not good for multiclassification problem

## Gaussian NB
Pros: Gaussian NB is fast to train and predict. Accurate like Random Forest(more or less). After Logistic regression, the lightest model. Also, much more lighter than RF. 

Cons: In this case less accuracy then RF

## SVM
Pros: Model size is light 

Cons: SVM very slow to train and prediction. Very low accuracy

## KNeighbors Classifier
Pros: Accuracy is not bad if we compare with others. 

Cons: Largest model. Train and prediction is slow

## K-Means

Pros: High accuracy if compare with other models

Cons: If class_0 cost is high not good model to use

## As written in the assignment, class_1(signal) is important to predict. Best model is K-Means

Please note that, That notebook trained on Python 3.9. If you are using Python 3.9, pickle is already exist but if you have less than python 3.9 you have to install pickle package.
