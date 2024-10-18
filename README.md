# Supplier Recommendation System
## Project Summary
This project is to give viable supplier suggestions to businesses that have unique requirements and restrictions.
For this project, I looked into two types of recommendation systems:
Content-based recommendations, which estimate item utility based on previous user preferences. Information about the users and the items they prefer is important.
- Limitations include: overspecialization and limited exploration of interests
Collaborative filtering, which defines k-closest users to current user and bases recommendation on other users’ preferences. This does not require additional information about users or items themselves.
- Limitations include: cold start problem, unlikely to recommend new items as not enough users have tried it, and insufficient data for identifying neighboring users

For this project, I decided to incorporate aspects of both content-based and collaborative filtering. The main concept used is matrix factorization, which is a collaborative filtering technique. Usually, companies are looking for specific suppliers that are well known within a community and match their specific needs. However, in order to counter the cold start problem and the possibility of insufficient neighbors, it is important to use attributes of companies and suppliers to help the model improve predictions.

Matrix factorization works by taking a sparse user-item matrix and breaking it down into lower-dimensional matrices that capture hidden features. It works well on sparse data, which is likely the case in business-supplier matrix.

I tested two types of matrix factorization that combine aspects of collaborative and content filtering:
- Alternating Least Squares (ALS) algorithm, which can incorporate implicit data to make predictions. Since the algorithm is not designed to handle additional features, I created a weighted combination of features based on the importance a company might place on supplier attributes such as quality and serviceability.
- Factorization machines, which build on matrix factorization to incorporate additional features like user demographics
To test the accuracy of results, I used the Normalized Discounted Cumulative Gain @ K metric.
- The best NDCG value with ALS after running several tests and optimizing hyperparameters was 0.08. This suggests that the model is not able to accurately align predictions to the actual order of relevance.
- The best NDCG value with factorization machines was 1. This suggests a perfect alignment between predictions and the actual order of relevance. The generated data might have been too simple for the model and real-world data would introduce more complexity, but this model proves the most promising.

## Motivation and Goal
Businesses often struggle with finding suppliers that meet their needs due to their specific requirements. While many companies may have general requirements for their suppliers such as quality and dependability, they can differ in terms of required proximity to manufacturing facilities, level of communication, and efficiency of delivery. There are even differences in level of quality and dependability a company is willing to sacrifice due to budget constraints and the business model. The concept of specificities making it hard to find tailored items is not unique to businesses, however; it is the same problems that many streaming, gaming, and social media platforms face. Every person is unique and the content delivered to them should be tailored to their preferences.
My goal is to approach the idea of supplier recommendations with a similar mindset, and to test if recommendation systems can be used to help businesses find ideal suppliers.

## Tools and Datasets
### Tools:
- Numpy
- Pandas
- Scikit-learn
### Datasets:
Synthetic data (supplier data not publicly available from my research)

## Limitations and Next Steps
While factorization machines proved to be a useful technique, it is not known for sure if it will as well on real-world data. The bigger issue is that it might be hard to collect data from several businesses related to suppliers and store it on a publicly available platform. Businesses themselves should have the incentive to store and share supplier data in order to improve their own prospects.
