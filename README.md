# Loan Prediction
To predict whether a loan will be default or not
 1) EDA with y-data profiling
 2) Handling imbalanced data
 3) Compare ensemble methods
 4) Discuss classification report
 5) Discuss three questions/hypothesis given in the class

Questions:
 1). The higher the installment the more likely to default
 2). Individual vs Join application (application_type), which one is more likely to default?
 3). The higher the credit limit the more likely to default

# Annotations & Sample Outputs

Features with outliers
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/ce916150-8a65-4b75-983d-966b831ebb57)

After transform
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/6c458a16-babb-4159-af69-5f8d667d4d3a)

Algorithm Comparison
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/323e2466-590d-4be6-a1e4-7d0058fff21a)

Classification Report
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/b22fad73-04b7-4176-b3cd-0ac1fa666073)

Confusion Matrix
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/031f737c-a2e1-42e9-91fc-bbad9210db3e)

Feature Importances
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/086c0ae4-7931-4876-85b9-1f921bd85278)

Partial Dependency Display
 ![image](https://github.com/mahdiwf/loan-prediction/assets/163992115/f69cbc13-5f54-4879-a4f9-2811ddc5c7ca)

To answer the questions/hypothesis asked in the assignment:
Partial dependence plots show how each variable or predictor affects the model's predictions.
 1). The higher the installment, the more likely the customer will not able to fully pay. This makes sense, but to be more contextual probably we could analize the data more details such as comparing with the income.
 2). Join application seems more likely to default. Perhaps, they are unfortunately separated/divorced? or they pass the responsibility to each other?
 3). High credit customer more likely to default. Again, we need to check more data to conclude, but probably higher credit limit will loan higher amount, resulted for them not able to pay.
