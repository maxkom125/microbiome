# microbiome project
### Authors: Artem Komarov, Maksym Komarov

### Intoduction
A consortium of microbiology labs is working to catalog the abundance of all known bacterial species in a large number of different environments (terrestrial, aquatic, associated with humans, animals or plants, etc...).  
The objective of this project is to use their data to build a machine learning model predicting the 1
environment in which a sample (described by a vector of abundances of the different bacterial species) has been collected.

### Feature selection, data preprocessing
The main problem addressed in this project was the high dimensionality of the microbiome data, which can make it difficult to accurately classify samples and identify important features. To solve this issue, we used feature selection technique - chi-squared stats between each non-negative feature and class to reduce the number of features in the database.

### Model selection
After feature selection was done, we trained different classifiers on this reduced dataset. For our experiments we used: `RidgeClassifier` and `SGDClassifier`. Both classifiers were able to achieve an accuracy up to **89%** on the test data, which demonstrates that the feature selection approach was effective. The exact results you can see below, or in the code.

The `RidgeClassifier` is a linear classifier that uses the Ridge Regression algorithm to minimize the sum of squared residuals.  
The `SGDClassifier` is a linear classifier that uses the Stochastic Gradient Descent algorithm for optimization.  
The main reason for choosing these classifiers is that Ridge Regression and SGD are both linear models suitable for large datasets, and can work good with high-dimensional data. Ridge Regression is a regularized linear regression model, which works well with correlated features, and prevents overfitting. SGD is a linear classifier that uses the Stochastic Gradient Descent algorithm for optimization, which is particularly useful for large datasets, and can also handle a large number of features, which is suitable for our high-dimensional data.

### Results
#### Results table 1: features number 1000
| Classifier        | Train Accuracy | Test Accuracy |
| ----------------- | --------------- | -------------- |
| RidgeClassifier   | 88.6%           | 86.3%          |
| SGDClassifier     | 84.8%           | 82.7%          |

In addition to the above experiment, we also repeated the same experiment for different number of remaining features. One of the best results of this experiment are shown in the table below:

#### Results table 2: features number 4000
| Classifier        | Train Accuracy | Test Accuracy |
| ----------------- | --------------- | -------------- |
| RidgeClassifier   | 94.1%           | 88.4%          |
| SGDClassifier     | 90.0%           | 87.8%          |

#### Conclusion
To sum up, our Microbinome project was successful in reducing the number of features in the dataset and achieving a high accuracy with the classifiers. This approach can be useful in other similar datasets with high dimensionality, where feature selection can improve the performance of classification models. Also, we faced with overfitting problem, which can be found in the second resuls table for the RidgeClassifier.

#### Code
The code can be found in dataset_investigation.ipynb file.
