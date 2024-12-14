### Consumer Purchase Behavior Trends

(Note this is still WIP as this is just the inital pass as requested in Capstone Project 20.1 Assignment - will fully complete in a later module)

**Author**
Abby Wilson 

#### Executive summary
We are trying to determine what attributes of a consumer most dictate how much they end up spending and on what, based on Consumer Behavior and Shopping Habits dataset. 

#### Rationale
I work with a lot of small business owners and understanding the factors that lead to the amount and type of purchases made is crucial in finding new audiences that will be most likely to buy their products and help grow their business. 

Essentially, it will help inform their product development and marketing strategies to ensure they are developing and marketing products that will sell.

#### Research Question
What attributes of a consumer most dictate how much they end up spending and on what?

#### Data Sources
I will use the Consumer Behavior and Shopping Habits Dataset[https://www.kaggle.com/datasets/zeesolver/consumer-behavior-and-shopping-habits-dataset]from Kaggle.

#### Methodology
Full Jupyter Notebook: https://github.com/AbbyWilson/Consumer-Purchase-Trends/blob/main/Capstone%20Analysis.ipynb

For the purchase amount, I will probably use some sort of linear model because the output is not a binary but rather a varying amount. 

For the item purchased, I will use a classification algorithm like K-nearest neighbors as this is a category based output. 

#### Results
For the purchase amount question, the best model was the Linear regression using polynomial features. This had a test MSE of 0.21. As can be seen in the purchase_amt_results.png in the results folder, for each Y Actual, we had a range of Predicted Y's that varied around the true value. Based on examining the coefficients of the model and looking at feature permutation, we can determing that the Review rating, subscription, location, and category of item are the key factors in determining purchase amount. 

For the item purchased question, the best model was the KNN Model. None of the models were very accurate here, likely due to not having enough data for each category. In fact, the score of the KNN model is very poor - only having an accuray of 0.05 which means that in only 5 out of 100 times did we predict the label correctly. You can see full predictions vs. actual in the item_purchased_results.png in the results folder. This is a case where we would need to finetune our model and likely gather much more data to have a more meaningful prediction. Nevertheless, we can still use the model training to directionally indicate which feature are most influential on the outcome. In this case, the location and gender are the most important features. This makes intuitive sense based on what I know about consumer behavior depending on where people live and their gender.

#### Next steps
What suggestions do you have for next steps?

#### Outline of project

- [Link to notebook 1]()
- [Link to notebook 2]()
- [Link to notebook 3]()


##### Contact and Further Information

Abby Wilson, abbywilson95@gmail.com