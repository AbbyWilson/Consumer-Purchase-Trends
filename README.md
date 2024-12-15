### Consumer Purchase Behavior Trends

**Author**
Abby Wilson 

#### Executive summary
**Project Overview and Goals**
Based on Consumer Behavior and Shopping Habits dataset, we are trying to determine what model best determines purchase amount and category and from this model, what attributes of a consumer most dictate how much they end up spending and on what category of item. This information will be used to make important business decisions, from marketing to product development to enhacing customer satisfaction. The models themselves can be used, after further refinement and data collection, to continue updating these predictions to make decisions both in real time and for the future. 

**Findings** 
The best model for predicting amount purchased is a Ridge Model, which had a train Mean Squared Error (MSE) of 565.29, a test MSE of 576.01, and a fit time of 0.001 seconds. We learned from this model that the top 5 influential features on determining purchase amount are location, color, season, payment method, and shipping type. This has meaningful business implications regarding where to invest resources on consumer sentiment (i.e. what payment methods and shipping types do you offer), demographics to develop clothing for and serve ads to (i.e. focusing on the top spending location and colors), as well as strategies for seasonality (i.e. differentiate offerings based on season, adjust marketing budget for seasonality). 

The best model for predicting the category of item purchased is a Random Forest Classifier, which had a training accuracy of 0.45, a test accuracy of 0.45 and a fit time of 0.52879 seconds. Although the test accuracy is a bit low here, we have to remember that the underlying data was a bit sparse across the categories, meaning there's a huge opportunity to improve this model with future data and refinement. Nevertheless, we learned that location and gender are the top influential features on what category a consumer purchases, which has meaningful implications on business decisions such as marketing, where to open up stores, and which item categories to continue investment in. 

**Next Steps**
In adition to using these findings and models in the ways detailed above, we will also want to invest resources to gather more data specific to the company that is going to be using these models. The data used here is publicly available, but a great next step would be for the company to invest in collecting and analyzing data specific to their own consumers as it will be more relevant. More relevant data means better models. Once we have that, we'll also want to finetune the models to ensure we are continuing to increase scores and lower error. And lastly, we'll want to build this into an ongoing process such that our models are continually learning and improving to inform business decisions.

#### Rationale
I work with a lot of small business owners of e-Commerce sites. Understanding the factors that lead to the amount and type of purchases made is crucial in driving more revenue, via informing their product development, marketing strategies, and customer satisfaction to ensure they are developing and marketing products that will sell and make people happy.

Given that a lot of these small business owners do not track a lot of their own data, starting with a public dataset helps to get initial insights and prove out the value of this type of strategy. Once that is proven, they will be more likely to invest in data collection and analysis to further refine these models and continue iterating on the process, as described in 'Next Steps' in the section below. 

#### Research Question
What is the best regression and classification model to predict how much consumers will end up spending and on what, and what does this model tell us about the features that are most relevant in dictating the purchase amount and category. 

#### Data Sources
I will use the Consumer Behavior and Shopping Habits Dataset[https://www.kaggle.com/datasets/zeesolver/consumer-behavior-and-shopping-habits-dataset]from Kaggle.

This dataset contains various information about consumers such as demographics, purchase history, preferences, and frequency of purchases.

**Initial Data Exploration**
As can be seen in the Data Exploration Jupyter Notebook, I first explored the data to see how balanced it is and which features appear to be correlated. All of the relevant plots can be found in the 'data_visualization' folder. There is a detailed listing of all the findings at the end of the Data Exploration Jupyter Notebook, but the high level takeaway is that the data is quite evenly distributed and we were not able to tell yet which features may impact purchase amount or category purchased, so building an AI model will be necessary here to find these influential features. The other important note is that the data for Category Purchased is a bit sparse and skewed towards the 'Clothing' category. This will be important when we dive into the model's findings later.

**Data Cleaning**
To clean the data, I dropped missing columns, converted "Yes/No" booleans to 1/0, and dropped columns that were not relevant to the model at hand. There was further scaling and transforming of the data, but this was implemented as a Pipeline with the model, so I will discuss in the following section. 

#### Methodology
Holdout cross validation was used for both purchase amount and category.

**Purchase Amount Regression Models**

**Simple Linear Regression** 
Using a Pipeline, I transformed and scaled the data as needed for Linear Regression, and used a Grid Search to try out various different hyper parameters for the Linear Regression model. 

**Linear Regression with Polynomial Features**
Using a Pipeline, I transformed and scaled the data, transforming the numeric ones into Polynomial Features. I then Grid Searched to test out various hyper parameters of the Linear Regression model.

**Ridge Model**
Using a Pipeline, I transformed and scaled the data and the Grid Searched to try out various hyper parameters of the Ridge Model. 

**Category Purchased Classification Models**

**Logistic Regression**
Using a pipeline, I transformed and scaled the data using OneHotEncoder and StandardScaler and then grid searched to test out various hyper parameters of the Logistic Regression model. 

**Decision Tree**
Using a pipeline, I transformed and scaled the data using OneHotEncoder and StandardScaler and then grid searched the various hyper parameters of the Decsion Tree model. 

**KNN**
Using a pipeline, I transformed and scaled the data using OneHotEncoder and StandardScaler and then grid searched the hyper parameters of a K Nearest Neighbors Model. 

**SVC**
Using a pipeline, I transformed and scaled the data using OneHotEncoder and StandardScaler and then grid searched the hyper parameters of a SVC Model. 

**Random Forest**
Using a pipeline, I transformed and scaled the data using OneHotEncoder and StandardScaler and then grid searched the hyper parameters of a Randon Forest Model. 

#### Results

**Purchase Amount Model Results**

**Simple Linear Regression**
This model had a train MSE of 565.15, a test MSE of 576.94, and a fit time of 0.001.

**Linear Regression with Polynomial Features**
This model had a train MSE of 542.46, a test MSE of 597.7, and a fit time of 0.072.

**Ridge**
This model had a train MSE of 565.29, a test MSE of 576.01, and a fit time of 0.001.

**Findings**
Comparing the test MSE of the 3 models above, we can see that the Ridge Model performed best at predicting the purchase amount. As can be seen in the 'purchase_amount.png' in the results folder, for each Y Actual, we had a range of Predicted Y's that varied around the true value. Based on examining the coefficients of the model and looking at feature permutation, we can determine that the location, color, season, payment method, shipping type, and size were all among the top influential features determining purchase amount.

**Category Purchased Model Results**
Note all the scores below are accuracy scores. This is the chosen metric for the models because we will be using the results to inform product development and marketing, so getting it right is most important and there is not a preference to minimize false negatives or false positives. 

**Logistic Regression**
This model had a train score of 0.47, a test score of 0.42 and a fit time of 0.01191

**Decision Tree**
This model had a train score of 0.46, a test score of 0.44 and a fit time of 0.00281. 

**KNN**
This model had a train score of 0.55, a test score of 0.36 and a fit time of 0.001.

**SVC**
This model had a train score of 1.0, a test score of 0.45 and a fit time of 0.21411.

**Random Forest**
This model had a train score of 0.45, a test score of 0.45 and a fit time of 0.52879.

**Findings**
SVC and Random Forest tied in terms of test accuracy, but Random Forest had a lower train accuracy meaning it is less likely to be overfit, so I chose this as the best model and explored it further. It is not the strongest model. As can be seen in 'category_purchased.png' in the results folder, it does not predict any footwear or outerwear, skewing heavily towards clothing and a little bit to accessories. Because of my initial analysis of the data, I know this is likely because the underlying data is skewed heavily towards the 'clothing' category. 

Nevertheless, we can still use this model directionally to answer our business question of which features are most important. Based on our analysis above, we can see that the location and gender are the most important features. This makes intuitive sense based on what we know about consumer behavior depending on where people live and their gender. 

#### Next steps

1) Use the data we have found here to inform marketing strategy, product development, and increase overall customer satisfaction.
2) Collect the company's own data over time, in the same format that is used here that tracks various features and then what was purchased and for how much.
3) Use that data to re-train these models with a more substantive and relevant training set.
4) Fine tune the models to re-pick the top one.
5) Use the best model based to re-draw conclusions about the top influential features and re-adjust marketing strategy, product development, and customer satisfaction strategies based on this.
6) Continually iterate and check in on results and roadmapping on a quarterly basis. 

#### Outline of project

- Data Exploration Notebook: https://github.com/AbbyWilson/Consumer-Purchase-Trends/blob/main/Data%20Exploration.ipynb
- Purchase Amount Notebook: https://github.com/AbbyWilson/Consumer-Purchase-Trends/blob/main/Purchase%20Amount%20Model.ipynb
- Category Purchased Notebook: https://github.com/AbbyWilson/Consumer-Purchase-Trends/blob/main/Category%20Purchased%20Model.ipynb

##### Contact and Further Information

Abby Wilson, abbywilson95@gmail.com
