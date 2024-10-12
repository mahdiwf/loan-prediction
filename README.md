# Loan Prediction
This project is modified from Data Science class group project assignment. This project will be using classifications machine learning to predict whether a loan will default or not. 
This is an introductory project in data science. However, we will use big volume data and y-data profiling for data analysis:
1) EDA with y-data profiling
2) Handling imbalanced data
3) Compare ensemble methods
4) Discuss classification report
5) Discuss three questions/hypotheses given in the class

Questions/hypothesis:
1) The higher the installment, the more likely the default.
2) Individual or Join application (application_type), which one is more likely to default?
3) The higher the credit limit, the more likely the default.

# Annotations & Sample Outputs

Data Size <br>
![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/c555ed3c-d16f-44ca-934b-6e7fcc43ed32)

It consists 66388 rows & 150 columns. Because of the size, we use y-data profiling for exploratory data analysis.

Processing data with y-data profiling
![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/0ee395cf-7d5f-4d8d-8d03-6a88d1fc06d7) <br>

y-data profiling produced a profile report in HTML with a size of about 600,000 KB. It is a very big report, through and details!. After reviewing these reports, we proceeded with the following steps.
 * remove columns (such as too many missing values, etc)
 * combine columns/create new features and remove old ones (feature engineering)
 * remove columns having low/zero correlation with the target

Now, we have a clean data after EDA above. However, there are still two problems with this data that has not been addressed in the above steps: outliers & imbalance data.

Finding & transform outliers<br>
Features with outliers (before transform)

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/ce916150-8a65-4b75-983d-966b831ebb57)

 While most valules are near zero, Some values/outliers as high as multiply of 1000000 (1e6). Outliers can significantly impact machine learning models, skewing data and leading to inaccurate predictions.
 Therefore, we will transform these values using numpy logaritmic function, np.log().

Features with outliers (after transform)

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/6c458a16-babb-4159-af69-5f8d667d4d3a)

Now, as the outliers have been transformed, we will handle the next problem.<br>

Handling Imbalance Data

![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/24d0ea04-b17d-4ddd-9b38-c32632f4e0c3) <br>

We use ADASYN to handle this imbalanced data. ADASYN is adaptive (GMAT is adaptive too!). Instead of all the samples being linearly interpolated (such as SMOTE), it adds random small values to the points, making it more realistic.<br>

After ADASYN

![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/fc1d4dc0-f07e-43ac-b1ca-6c6a6d78b720)


Algorithm Comparison

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/323e2466-590d-4be6-a1e4-7d0058fff21a)

From this result, Random Forest (RF) performed better than Ada Boost & Gradient Boosting Method.

Classification Report

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/b22fad73-04b7-4176-b3cd-0ac1fa666073)

Wow, the classification report shows a perfect score. In theory, this model predicts with almost 100% accuracy! I am sure some form of overfitting may existed.
In the future/next project, I will prepare unseen data from the dataset to run the model to see how much overfitting occurs.

Confusion Matrix

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/031f737c-a2e1-42e9-91fc-bbad9210db3e)

Since I want to identify the likelihood of being charged off (bad loan), the Positive class is 'charged off,' and the negative class is 'fully paid.'
* False Positive = 0 vs. True Positive= 10906. 
The model has zero mistakes in identifying the charged-off. It doesn't identify any 'fully paid' as 'charged off.'
* False Negative= 14 vs. True Negative= 10414. 
Here, the model has missed 'fully paid' by identifying them as 'charged off', but there are only small number (14) compared with the total accounts (10428).

Again, in theory, this is a good result.

Feature Importances

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/086c0ae4-7931-4876-85b9-1f921bd85278)

This shows the 10 most important factors for this prediction. Some of these features intuitively tell us that it is a major factor such as the last payment amount, installment size, and loan amount.

Partial Dependency Display

 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/f69cbc13-5f54-4879-a4f9-2811ddc5c7ca)

To answer the questions/hypothesis asked in the assignment:
Partial dependence plots show how each variable or predictor affects the model's predictions.
1) The higher the installment, the more likely the customer will not pay. It seems to make sense, but we could analyze the data deeper by comparing the installment with the income. We will have a better context.
2) The join applications seem more likely to default. Are they unfortunately separated/divorced after the application? Do they pass the responsibility to each other? Some reasons I can think of.
3) High-credit customers are more likely to default. A higher credit limit will likely loan a higher amount. This makes them not being able to pay.

References:<br>
https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html <br>
https://www.tutorialspoint.com/compute-classification-report-and-confusion-matrics-in-python <br>
https://www.kdnuggets.com/2017/06/7-techniques-handle-imbalanced-data.html <br>
https://www.quora.com/In-classification-how-do-you-handle-an-unbalanced-training-set/answers/1144228?srid=h3G6o <br>
https://dev.to/thalesbruno/subplotting-with-matplotlib-and-seaborn-5ei8 <br>
https://www.kaggle.com/code/dansbecker/partial-dependence-plots <br>
