# Final Project COG118A
Abstract:
There are many types of machine learning algorithms and all of them have their strengths and weaknesses. This paper compares three of them: Decision Trees, Random Forest Classifiers, and Support Vector Machines (SVMs) using datasets from the UCI Machine Learning website. This paper also studies different partitioning techniques in order to determine which is the best split for training and testing data. It was found that the best split for training and testing data was to have a greater amount of training data than testing data. It was also found that Decision Trees and Random Forest Classifiers performed better than SVMs on the datasets studied.

Introduction:
This project is an empirical study on different types of machine learning algorithms that were covered in the Cogs 118A Machine Learning class. Often times it is hard to compare machine learning algorithms learned in lecture because the homeworks cannot be entirely comprehensive. This project provided the author with the chance to pick and choose their own algorithms and datasets to fully engage with the models presented in class. This project was looking at how different machine learning models perform on different sized datasets. The goal was to either support or contradict some of the results in Caruana and Niculescu-Mizil’s paper: “An Empirical Comparison of Supervised Learning Algorithms”. In particular, it was expected that when partitioning the data between testing and training, algorithms would be more accurate when the amount of training data was greater than or equal to the amount of testing data. It was also expected that Random Forests would be more accurate than SVMs which would be more accurate than Decision Trees given that those were the results of Caruana and Niculescu-Mizil’s paper.

Methods
Learning Algorithms Used:
Machine learning algorithms were picked that would perform differently on the datasets to show their different strengths. Additionally, these algorithms were picked because they are fast and do not take a huge amount of computational time as the analysis was run on a laptop.
SVM:  SVM with a linear kernel was included because it is a high performer compared to other machine learning algorithms. 
Decision Tree: Decision Tree was included because it is usually one of the worse machine learning algorithms and it was interesting to test to see if this were the case with all the datasets.
Random Forest Classifier: Random Forest(RF) Classifier was included to test to see if they perform better than Decision Tree algorithms since RFs are an aggregation of decision trees. 

Comparing Across Performance Metrics:
The performance metric used was accuracy on the test dataset. 

Calibration Metrics:
For each machine learning algorithm used, there were hyperparameters that were tested. 
For the SVM model, the hyperparameter was the C value, the penalty parameter of the error term. According to the SciKit-Learn website, the noisier the data, the smaller this parameter should be. The list of C values tried was [0.00001, 0.0001, 0.001, 0.01, 1].
For both the Decision Tree model and the Random Forest model, the hyperparameter used was the max-depth value. The range tested was [1, 2, 3, 4, 5, 6]. These models are both prone to overfitting, so the maximum depth needs to be kept short.

Cleaning and Prepping the Data Sets:
 1. The first dataset used was the Mushroom Dataset from the UCI Machine Learning 
website. There are 22 attributes in this dataset which are all used to classify a poisonous mushroom or an edible mushroom. The features were classifications like ‘cap-size’ and ‘gills’. Several rows were dropped in this dataset as there was missing data. The number of datapoints for one classification was around 3500 and for the other classification there were around 2160 data points. One-hot encoding was used to prep the data for the machine learning algorithms as all the features were categorical data.
2. The second dataset was the Breast Cancer Wisconsin Dataset. This dataset predicts malignant tumors versus benign tumors. There are 8 attributes in this data. This dataset also had a few rows that were dropped because of missing data. The number of datapoints for one classification was around 400 data points for one classification and 200 data points for the other classification. This is a much smaller dataset than the first so it was suspected that the machine learning models would all perform worse with this dataset.
3. The third dataset was the Contraceptive Dataset. It has three classifications, whether a woman used no birth control, short-term birth control, or long-term birth control. It uses 9 features to predict those labels. Because there were three classifications, the long-term birth control class was dropped. This meant that there were around 630 data points for one classification and 222 data points for the other classification. This dataset was also small compared to the first dataset so it is suspected that the classification would be worse.
4. The fourth dataset used was the Adult Dataset. This dataset was collected census data which classified whether or not someone earned above or below 50k. The dataset was chosen to contrast with the other datasets because it is the largest dataset, with around 30,000 data point. There were also many attributes in this dataset; with one-hot encoding, the number of attributes was around 113.

*All datasets were found on the UCI Machine Learning website

Implementation of Machine Learning Algorithms:

All the machine learning models were drawn from the Scikit-Learn website. Besides using their methods for Decision Tree, Random Forest, and SVM, the GridSearchCV method was also used. The GridSearch method tested the hyperparameters and also performed the cross validation and 3 k-fold techniques with the classifiers.
For each dataset, the following steps were performed:

Choosing a classifier
Splitting up the data into testing and training
Initializing a classifier
Initializing a GridSearch with the list of hyperparameters
Training the classifier using the output of the GridSearch
Drawing a heatmap of the hyperparameters 
Training a new classifier with the hyperparameter that returned the highest accuracy
Using the new classifier to predict labels on the test set
Repeat 1 - 8 for each classifier
 Repeat 9 for each testing and training partition

Results:
The following tables shows the accuracy (rounded to the third decimal) of the machine learning models on each dataset as well as the average accuracy for each model and testing/training partition.





Accuracy Results of Machine Learning Algorithms on Cancer Dataset
* I removed the results since tables take up a huge amount of space in this file

*SVM did not finish in a time that was reasonable for this dataset.

Conclusions:

The two methods that were being tested were how partitioning up the data affected accuracy and how different machine learning models performed on the datasets. 
Partitioning Discussion:
The results for how partitioning the data affected accuracy were clear; 80% training and 20% testing performed the best, with 50% testing and 50% training following close behind and 20% training and 80% testing performing the worst. 80% training and 50% training were relatively close to each other, while 20% training was far behind. This supports the initial reasoning that it is better to have more training data than test data. 
Machine Modeling Discussion:
The results for the machine modeling comparison were less clear. Decision Trees and Random Forests were tied for the most accurate, and SVMs came up last. This was surprising as Decision Trees were expected to perform the worst. It is suspected that this has to do with how different the datasets were from each other and one of the datasets(the Adult dataset) was so large that the SVM algorithm never finished running. The consistent top performer was the Random Forest Classifier, but the Decision Tree performed much better than expected. So although the partitioning results were as expected, the results from the paper by Caruana and Niculescu-Mizil were unable to be exactly reproduced. 


References:

Caruana, Rich, and Alexandru Niculescu-Mizil. “An Empirical Comparison of Supervised Learning Algorithms.” Https://Www.cs.cornell.edu, Cornell, 2006, www.bing.com/cr?IG=A648D49C8A4C4D4F886E544DFDC94E6A&CID=2DEA4C9BC749624E0FCA4727C6EF6321&rd=1&h=zrBtzR-2ZkoEojJOWFJdUKY7HLRwNoNizzNi37gPzJk&v=1&r=https%3a%2f%2fwww.cs.cornell.edu%2f%7ecaruana%2fctp%2fct.papers%2fcaruana.icml06.pdf&p=DevEx,5066.1.

Scikit-learn: Machine Learning in Python, Pedregosa et al., JMLR 12, pp. 2825-2830, 2011.

