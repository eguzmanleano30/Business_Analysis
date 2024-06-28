# Business Analysis of the Personal Care and Beauty Market  

# Case Sephora Beauty Retailer  
**Edward Guzman Leano**

**eguzmanleano30@gmail.com**

## Justification for the Project:

The main objective of this project is to develop an knowledge of the requirements of Sephora’s clients, analyze opportunities that can be exploited, and weaknesses that can be avoided from online sales. 

The purpose is show that the SWOT methodology could be a helpful tool for developing a business strategy from complex business data as the personal care and beauty retailers.  

### Information of Company and data used
Sephora is a globally renowned multinational chain specializing in beauty and personal care products with a robust foothold, particularly within the U.S. market. Famous for its expansive online platform, Sephora has effectively capitalized on e-commerce trends, offering customers a seamless shopping experience and various products. Moreover, Sephora's innovative approach incorporates customer feedback mechanisms, allowing users to rate and endorse products, fostering a sense of community and trust among its clients.

https://en.wikipedia.org/wiki/Sephora

The Sephora data was obtained from Kaggle, an online community and platform for data scientists and machine learning practitioners to find and publish datasets, explore and build models, and compete in data science challenges. This dataset is valuable for projects involving market analysis, consumer behavior studies, and trend analysis in the beauty industry. Sephora's data – with 21 variables and 91,658 observations – provides essential insights into its product offerings online. This information discloses valuable insights into Sephora's product lineup, customer preferences, and marketing strategies. 

https://www.kaggle.com/datasets/raghadalharbi/all-products-available-on-sephora-website/data

## Formulation of questions about the requirements of clients: 

### First research question 

What factors drive customers to shop online instead of in-store at Sephora?  

**Explanation of research question** 

This research question delves into the factors influencing customers’ purchase decisions between shopping online and in-store at Sephora. It seeks to identify the key product characteristics and customer preferences that lead individuals to shop online rather than visiting physical stores. 

### Second research question 

Which factors influence the level of customer love for products sold on Sephora’s website?   

**Explanation of research question**

This research question investigates the factors contributing to the level of customer love for products available on Sephora’s website. The dependent variable, ‘love,’ represents the number of people who love a particular product, indicating customer satisfaction and affinity towards the product. 


## Method Section. 

### Exploratory Data Analysis (EDA) 

Before conducting any business or data analysis, we will examine data to identify patterns, detect anomalies like missing values, and gain insights through visualizations and summary statistics. Additionally, we will transform all variables that do not exhibit a standard distribution to achieve a normal pattern. All EDA processes are detailed in the following link. 

[Exploration Data Analisis of Sephora data](Exploration_data.md)


### Logistic Regression Analysis for Online Shopping Preferences 

The project's next phase involves building a Logistic Regression model with the variable online_only that addresses the first research question. The variable indicates whether a product is exclusively available through Sephora's online platform. Given the binary nature of the outcome variable (online shopping vs. in-store shopping), logistic regression is the appropriate model for estimating the probability of a customer shopping online based on various predictor variables. The method is grounded in selecting variables that contribute meaningfully to the model's predictive power while avoiding overfitting and ensuring clinical relevance. The entire logistic regression model-building process is detailed in the following link.

[Logistic regression model for online sells](Logistic_regression.md)

### Multiple Linear Regression Analisis for customer who love a beauty produc

We will employ multiple linear regression as our primary analytical tool to respond to the second question: Which factors influence the degree of customer affinity towards products available on Sephora's website? This methodology will help to analyze the factors influencing customer love for products sold on Sephora's website. Likewise, it allows us to examine the relationship between multiple predictor variables and the outcome variable, which is the level of customer love. The entire mutiple linear regression process is detailed in the following link.

[Multiple Linear Regressio](Linear_Regression.md)





