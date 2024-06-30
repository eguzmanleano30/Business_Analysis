## Business Analysis of the Personal Care and Beauty Market  

## Case Sephora Beauty Retailer  
**Edward Guzman Leano**

**eguzmanleano30@gmail.com**

### Justification for the Project:

The main objective of this project is to develop an knowledge of the requirements of Sephora’s clients, analyze opportunities that can be exploited, and weaknesses that can be avoided from online sales. 

The purpose is show that the SWOT methodology could be a helpful tool for developing a business strategy from complex business data as the personal care and beauty retailers.  

### Information of Company and data used
Sephora is a globally renowned multinational chain specializing in beauty and personal care products with a robust foothold, particularly within the U.S. market. Famous for its expansive online platform, Sephora has effectively capitalized on e-commerce trends, offering customers a seamless shopping experience and various products. Moreover, Sephora's innovative approach incorporates customer feedback mechanisms, allowing users to rate and endorse products, fostering a sense of community and trust among its clients.

[Sephora information](https://en.wikipedia.org/wiki/Sephora)

The Sephora data was obtained from Kaggle, an online community and platform for data scientists and machine learning practitioners to find and publish datasets, explore and build models, and compete in data science challenges. This dataset is valuable for projects involving market analysis, consumer behavior studies, and trend analysis in the beauty industry. Sephora's data – with 21 variables and 91,658 observations – provides essential insights into its product offerings online. This information discloses valuable insights into Sephora's product lineup, customer preferences, and marketing strategies. 

[Data source](https://www.kaggle.com/datasets/raghadalharbi/all-products-available-on-sephora-website/data)

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

The project's next phase involves building a logistic regression model with the 'online_only' variable as the response to address the first research question. This variable indicates whether a product is available exclusively on Sephora's online platform or in-store. Given the binary nature of the outcome, logistic regression is the appropriate method to estimate the probability of a product being offered online based on various predictor variables. The detailed process of constructing the logistic regression model is outlined in the following link.

[Logistic regression model for online sells](Logistic_regression.md)

The final logistic regression model for predicting the likelihood of a product being online-only is expressed as:

**G(online_only)** = 3.64-1.26*limited_edition -1.61*exclusive-0.97*log_price + 0.9*log_value_price -0.55limited_edition*log_price +0.44exclusive*log_price

### Multiple Linear Regression Analisis for customer who love a beauty products

We will employ multiple linear regression with the 'love' variable as the response to address the second research question. This variable measures customer interest in a product by tallying the number of users who have expressed affection or favorited the item. This methodology will help analyze the factors influencing customer love for products sold on Sephora's website and examine the relationship between multiple predictor variables and the outcome variable. The detailed process of constructing the multiple linear regression model is outlined in the following link.

[Multiple Linear Regressio](Linear_Regression.md)

The final linear regression model for predicting customer love is expressed as:

_**log(love)** = 5.87 + 0.08 x rating + 0.68 x log(number_of_reviews) - 0.81 x Log(price) ​+ 0.66 x Log(value_price) + 0.31 x exclusive + 0.28 x limited_edition​_

This model indicates that customer love, as measured by the number of users who have favorited a product, is positively influenced by the product's rating, the log of the number of reviews, the log of the value for price, exclusivity, and limited edition status. Conversely, it is negatively influenced by the log of the price. This regression model helps identify the key factors that significantly contribute to customer interest and preference for products on Sephora's website.


## SWOT analysis of Sephora 
### Interpretation of coefficient for logistic regression model
The logistic regression analysis highlights key strengths and weaknesses affecting the likelihood of products being online-only on Sephora's platform. Strengths include better value-for-price perceptions and the positive interaction of exclusivity with higher prices, both of which increase online-only availability. Weaknesses include limited edition and exclusive products, and higher prices, all reducing the likelihood of online-only availability. Additionally, limited edition status combined with higher prices further limits online accessibility. 



| **Opportunities (Strengths)**                       | **Coefficient** | **Interpretation**                                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Log(Value for Price)                 | 0.9             | Each one-unit increase in log(value for price) increases the log-odds of being online-only by 0.90. This suggests that products perceived as offering better value for their price are more likely to be exclusively available online. This can attract price-sensitive customers who seek value in their purchases.                                    |
| Interaction: Exclusive \* Log(Price) | 0.44            | The positive interaction effect between being an exclusive product and the logarithm of price indicates that for exclusive products, the negative impact of higher prices on the likelihood of being online-only is mitigated. This enhances the attractiveness of exclusive items for online shoppers who may perceive them as worth the higher price. |


| **Weaknesses (Threats)**                                   | **Coefficient** | **Interpretation**                                                                                                                                                                                                                                                                                                                                                     |
| ---------------------------------------------------------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Limited Edition                             | \-1.26          | Limited edition products are less likely to be available exclusively online, as the negative coefficient indicates. This limits the accessibility of these products to online customers, potentially missing out on online sales opportunities and restricting customer reach.                                                                                         |
| Exclusive                                   | \-1.61          | Being an exclusive product decreases the log-odds of being online-only by 1.61. This suggests that while exclusivity can enhance perceived value, it may reduce the likelihood of online-only availability, limiting accessibility and potentially missing out on online customer engagement.                                                                          |
| Log(Price)                                  | \-0.97          | Each one-unit increase in log(price) decreases the log-odds of a product being online-only by 0.97. Higher prices make products less likely to be exclusively available online, potentially limiting accessibility to online shoppers who may seek more affordable options.                                                                                            |
| Interaction: Limited Edition \* Log(Price)  | \-0.55          | The negative interaction effect between limited edition status and log(price) suggests that the impact of limited edition status on reducing the likelihood of being online-only is amplified for higher-priced products. This further restricts the availability of limited edition items to online customers, potentially missing out on online sales opportunities. |


### Interpretation of coefficient for linear regression model

The multiple linear regression analysis reveals key strengths (opportunities) and weaknesses (threats) in determining the factors influencing customer love for products on Sephora's website. Strengths include higher ratings, which increase customer love, and a more significant number of reviews, indicating that products with more customer feedback tend to be more loved. Products perceived to offer better value for their price also receive more affection, as shown by the positive coefficient for log(value for price). Additionally, customers favor exclusive and limited edition products, enhancing their appeal. On the other hand, weaknesses include higher prices, which decrease customer love, as indicated by the negative coefficient for log(price). This analysis helps Sephora strategically understand the factors that drive customer interest and love, allowing for better optimization of product offerings to enhance customer satisfaction and engagement.

| **Opportunities (Strengths)** | **Coefficient** | **Interpretation**                                                                                                                                                      |
| ----------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Rating                        | 0.08            | Each one-unit increase in rating increases the log(love) by 0.08, suggesting that higher-rated products receive more customer love.                                     |
| Log(Number of Reviews)        | 0.68            | Each one-unit increase in log(number of reviews) increases the log(love) by 0.68, indicating that products with more reviews tend to be more loved.                     |
| Log(Value for Price)          | 0.66            | Each one-unit increase in log(value for price) increases the log(love) by 0.66, suggesting that products perceived as offering better value receive more customer love. |
| Exclusive                     | 0.31            | Being an exclusive product increases the log(love) by 0.31, indicating that exclusive items tend to receive more customer affection.                                    |
| Limited Edition               | 0.28            | Being a limited edition product increases the log(love) by 0.28, showing that limited edition items are more favored by customers.                                      |


| **Weaknesses (Threats)** | **Coefficient** | **Interpretation**                                                                                                                               |
| ------------------------ | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Log(Price)               | \-0.81          | Each one-unit increase in log(price) decreases the log(love) by 0.81, indicating that higher-priced products tend to receive less customer love. |


