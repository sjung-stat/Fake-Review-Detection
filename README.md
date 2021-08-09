Fake Review Detection
================

> Investigating restaurant review/reviewer dataset and implementing classifiers to detect fake reviews



### Introduction

![](Image/Introduction_image.jpg "Title")


Modern people tend to read reviews before buying products or services for smart and wise spending in addition to information provided by businesses. But there are some cases where businesses intentionally don't provide consumers with information on downside of their products/services, or even make false and exaggerated advertisements in order to maximize their profits. For that reason, consumers don't accept the information unconditionally. However, they can obtain more accurate information from other consumers who have already used the services/products that they are interested in buying. So, direct evaluations from customers can give potential customers more credit. Therefore, according to this article [10 ONLINE REVIEW STATISTICS YOU NEED TO KNOW IN 2021](https://www.oberlo.com/blog/online-review-statistics) from Oberlo, "56 percent of consumers read at least four reviews before buying a product."

However, the number of cases where online reviews are abused is rapidly increasing. Some review writers leave false reviews so that consumers can't determine precisely. There are mainly two types of false reviews. First, malicious reviews written by rival businesses. By producing rumors through negative groundless reviews, they make negative public perceptions towards the business which, in turn, directly affects the business operation. According to an article [How Harmful Are Fake Online Reviews](https://www.business2community.com/infographics/how-harmful-are-fake-online-reviews-infographic-02316083) from Business 2 Community, a business "risks losing 22% of their online business if just one negative review is discovered by shoppers who are considering purchasing your product. If a business happens to have 3 negative reviews, they risk losing 59% of customers." Therefore, such fake reviews can be fatal to businesses. Second, overly exaggerated reviews left by business owners or people hired by the owners. By writing overly positive reviews that are not true in order to present a good image, they can give false positive perceptions to customers and attract them. But customers can get services/products that fall short of their expectations. In other words, both of the two types can cause harm to either businesses or customers by giving false information. For these reasons, filtering fake reviews to protect them is socially and economically very important. 


Yelp, which was founded in 2004, is an online platform that provides services for users to evaluate local businesses. People who have experienced can share their opinions (reviews). By sharing their opinions (reviews) based on their experiences on services or products of local businesses, they can help other users can easily decide whether to purchase or not. When leaving reviews, reviewers can give numerical rating (score) from 1 to 5 along with text reviews. Also, other users can upvote reviews if they find them useful, funny, etc. And users can make connections with each other within the website. Yelp filters fake reviews so that other users cannot see them. By doing this, Yelp builds up a trust between users and businesses, which helps increase the user number and raise dependence. In this project, I build classification models using Yelp dataset that detects and classifies fake reviews. 


-----

### About the Data

The dataset, which was scraped from Yelp, is consisted of approximately 27,000 rows with 30+ features. Each row represents reviews for restaurants in Chicago, Illinois and they also contain information of the reviewer and the restaurant. Among the 27,000 reviews, roughly 22% of them were filtered (the feature 'flagged' is the label in this dataset. It has two values, Y and N. 'Y' represents a fake, or filtered, review and 'N' represents a genuine, or unfiltered, review. Please refer to the separate file named "Yelp_Restaurant_Codebook" for more information about the other features). Since they contain sensitive  personal data, some features are dropped in the Data Cleaning section. For the same reason, I do not share the dataset publicly. In order to reproduce this project, please visit [here](http://liu.cs.uic.edu/download/yelp_filter/) and formally request the data. 



-----

### Method

- __[Preparation](https://github.com/sjung-stat/Fake-Review-Detection/blob/main/Data_Preprocessing.ipynb)__: The dataset scraped from Yelp are stored in a SQLite database which contains three tables. Using SQL queries, I join three tables, select features, and import the data. 


- __[Data Cleaning](https://github.com/sjung-stat/Fake-Review-Detection/blob/main/Data_Preprocessing.ipynb)__: This process includes handling missing values, mismatched data types, noisy data, sensitive information, etc. Also, text data (review contents) are cleaned for Natural Language Processing.


- __[Exploratory Data Analysis](https://github.com/sjung-stat/Fake-Review-Detection/blob/main/Exploratory_Data_Analysis.ipynb)__: Hidden trends or patterns are discovered by visualizing the data. It gives ideas for feature engineering. 


- __[Feature Engineering](https://github.com/sjung-stat/Fake-Review-Detection/blob/main/Feature_Engineering_and_Model_Building.ipynb)__: In this section, new features are created using the existing features to increase the accuracy of classifiers. For instance, it calculates the number of words and uppercase letters in the review contents. And it performs sentiment analysis (NLP technique) to obtain polarity and subjectivity scores. 


- __[Model Building](https://github.com/sjung-stat/Fake-Review-Detection/blob/main/Feature_Engineering_and_Model_Building.ipynb)__: Raw text data are used to build a classifier using NLP and Deep Learning techniques (CNN, LSTM). In addition, several machine learning algorithms are implemented based on other categorical and numerical attributes; XGBoost, Random Forest, Neural Network, Support Vector Machine, Logistic Regression, KNN. Accuracy, sensitivity, and specificity are used to measure the performance of each classifier. And three models are further developed by tuning hyperparameters to produce a better result.


-----

### Conclusion

A total of 6 classifiers are built as mentioned in the __Model Building__ subsection above. The following is the summary of the classification results based on 10-fold cross validations:

- XGBoost (Accuracy: 90.5% / Precision: 80.1% / Recall: 77.8%)
- Random Forest (Accuracy: 88.3% / Precision: 78.1% / Recall: 67.8%)
- Neural Networks (Accuracy: 87.3% / Precision: 72.9% / Recall: 70.1%)
- Logistic Regression (Accuracy: 84.9% / Precision: 70.7% / Recall: 58.7%)
- Support Vector Machine (Accuracy: 82.8% / Precision: 71.2% / Recall: 42.7%)
- SGD Classifier (Accuracy: 82.5% / Precision: 67.2% / Recall: 46.8%)
- KNN (Accuracy: 78.0% / Precision: 54.5% / Recall: 27.5%)

And the first three classifiers are optimized by finding the optimal combinations of hyperparameters through grid search. After the optimization process, the classifiers are improved as follows: 

- XGBoost (Accuracy: 90.8% / Precision: 80.9% / Recall: 78.6%)
- Random Forest (Accuracy: 89.6% / Precision: 79.5% / Recall: 74.1%)
- Neural Networks (Accuracy: % / Precision: % / Recall: %) - In Progress



-----

### Contact Information

  - If you have any questions, feel free to email me at
    <sjung.stat@gmail.com>
  - You can find my LinkedIn profile
    [here](https://www.linkedin.com/in/sjung-stat/)
