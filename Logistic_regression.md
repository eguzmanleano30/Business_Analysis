## Logistic Regression Analysis for Online Shopping Preferences 

### Research questions: 
What factors drive customers to shop online instead of in-store at Sephora? 

### Explanation of research question 
This research question delves into the factors influencing customers’ purchase decisions between shopping online and in-store at Sephora. It seeks to identify the key product characteristics and customer preferences that lead individuals to shop online rather than visiting physical stores. 

### Data information 
The data was obtained from Kaggle that is an online community and platform for data scientists and machine learning practitioners to find and publish datasets, explore and build models, and compete in data science challenges. This dataset is valuable for projects involving market analysis, consumer behavior studies, and trend analysis in the beauty industry. 

Methodology: Multiple Linear Regression for the Sephora Project 

We will employ multiple linear regression as our primary analytical tool to respond to the second question: Which factors influence the degree of customer affinity towards products available on Sephora's website? This methodology will help to analyze the factors influencing customer love for products sold on Sephora's website. Likewise, it allows us to examine the relationship between multiple predictor variables and the outcome variable, which is the level of customer love. 

Data Collection and Preparation: 

We will employ the outcomes derived from the Exploration Data Analysis (EDA) methodology to manage this part. Our approach will involve gathering data from Sephora's website, diligently cleaning and preprocessing it to handle missing values and outliers, and rigorously ensuring consistency across variables. 

Selection of Predictor Variables: 

We will select the predictor variables likely to impact the "love " response variable. These variables may include product attributes such as brand, category, ingredients, formulation, customer reviews and ratings, product price, promotional offers and discounts, product popularity and trendiness, seasonality, and special events. The regression model will include variables that are expected to have a significant impact on customer love. However, highly correlated variables will be evaluated carefully to avoid multicollinearity issues (Kutner, 2005). 

Sephora's dataset – with 21 variables and 91,658 observations – provides essential insights into its product offerings online. This information discloses valuable insights into Sephora's product lineup, customer preferences, and marketing strategies.
https://www.kaggle.com/datasets/raghadalharbi/all-products-available-on-sephora-website/data

### Building a logistic regression model for products sold online only
To build a logistic regression model, we will incorporate all independent variables. The aim is to predict the likelihood of a product being exclusively sold online on Sephora’s website. This model will enable Sephora to optimize its product assortment, marketing strategies, and distribution channels to maximize online sales and enhance overall profitability. Additionally, insights gained from the model can inform strategic decision-making and help Sephora stay competitive in the rapidly evolving e-commerce landscape. 

### _Univariable analysis_
The following table shows the univariable logistic regression analysis on the Sephora web platform dataset, revealing potential associations between various independent variables and online-only sales. Significant factors such as rating, limited edition, exclusive, log price, log value price, and log love may influence online sales, as is evident from their Wald test p-values below 0.25. In contrast, category, limited edition offers, and MarketingFlags show no significant associations with online-only sales.


**Univariable Analysis results**
| Indepen. Variable     | Coeffic. (B1) | Standard Error | Wald Test | P-value | conclusion                                        | Output and code |
| --------------------- | ------------- | -------------- | --------- | ------- | ------------------------------------------------- | --------------- |
| Category              | 0             | 1.782 e3       | 0         | 1       | No significant association with online-only sales | ![Appendix](        |
| Rating                | \- 0.083      | 0.0463         | \-1.801   | 0.0717  | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_Rating.pdf)        |
| limited edition       | 0.702         | 0.077          | 9.144     | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_limited_edition.pdf)        |
| Limited Edition Offer | \-10.384      | 113.719        | \-0.091   | 0.9275  | No significant association with online-only sales | ![Appendix](Logistic_Regression/Univaria_Analis_limited_edition_offer.pdf)        |
| Exclusive             | \-0.414       | 0.06026        | \-6.871   | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_Exclusive.pdf)        |
| MarketingFlag         | 19.54         | 156.68         | \-0.091   | 0.9     | No significant association with online-only sales | ![Appendix](Logistic_Regression/Univaria_Analis_MarketingFlag.pdf)        |
| Log Price             | 0.299         | 0.0357         | 8.385     | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_Price.pdf)        |
| Log Value Price       | 0.334         | 0.03506        | 9.544     | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_Value_Price.pdf)        |
| Log Love              | \-0.574       | 0.0193         | \-29.68   | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_love.pdf)        |

### Multivariable Logistic Regression Model Analysis for Online-Only Sales Prediction at Sephora 

Using several potential predictors, the multivariable logistic regression model was built to predict online-only sales at Sephora's website. The model equation indicates that limited edition, exclusive status, log price, log value price, and log love are considered predictors. The statistical summary reveals that limited edition, log price, and log value price have statistically significant coefficients, suggesting they may influence online-only sales. The intercept coefficient represents the log odds of online-only sales when all predictors are zero, which is 3.176. Overall, the model provides insights into the relative importance of various predictors in determining online-only sales for Sephora's products. 

Log odd: G(online_only) = 3.176 + 0.421*limited_edition - 0.306 exclusive -0.907 Log_price + 0.95 Log_value_price - 0.551 Log_love 

![Statistical summary of model with potential predictors](Logistic_Regression/model_with_all_predictors.pdf)

  | Independent variables | Coefficient | Standard Error | Z Value  | P-value  |
| --------------------- | ----------- | -------------- | -------- | -------- |
| Intercept             | 3.176       | 0.233          | 13.589   | 0        |
| limited_edition1      | 0.421       | 0.093          | 4.5      | 6.80E-06 |
| exclusive1            | \-0.306     | 0.067          | \-4.563  | 5.00E-06 |
| log_price             | \-0.907     | 0.239          | \-3.789  | 1.51E-04 |
| log_value_price       | 0.95        | 0.235          | 4.044    | 5.24E-05 |
| log_love              | \-0.551     | 0.012          | \-27.861 | 0        |


### Refinement of Multivariable Model 

The following table shows the iterative process of refining the multivariable model through stepwise elimination and assessment of likelihood ratio tests, which has provided insights into the predictors' significance for “online only” response. Predictors such as Log Love, Log Value Price, and Log Love have minimal impact on the model's performance, as evidenced by their elimination, which results in insignificant changes in deviance and confounder analyses. Therefore, the multivariable model is better than all reduced models. 


|   | Likelihood Ratio Test (LR)  |   |   |   | Confounder Analysis  |   |   |
| --------------- | ----------------- | --------- | ------- | -------------------------- | ----------------------------------------------------------------------------------- | -------------------- | --------------- |
| **Variable Remove** | **Residual Deviance** | **LR G** | **P-value** | **Conclusion  <br>Full model** | **Δβ%**                                                                                 | **Conclusion**           | **Output and code** |
| Log Love        | 9569.19           | 920.11    | 0       | Better model               | Limited Edition: 54.45  <br>Exclusive: 50.73 <br>Price: -6.77 <br>Value Price: 1.56 | Important confounder | ![Appendix](Logistic_Regression/Model_without_log_love.pdf)        |
| Log Value Price | 9592.74           | 943.66    | 0       | Better model               | Limited Edition: 93.87 <br>Exclusive: 45.7  <br>Price: -126.48                      | Important confounder | ![Appendix](Logistic_Regression/Model_without_log_value_price.pdf)        |
| Log Price       | 9635.28           | 986.2     | 0       | Better model               | Limited Edition: 99.96 <br>Exclusive: 73.06                                         | Important confounder | ![Appendix](Logistic_Regression/Model_without_log_price.pdf)        |
| Exclusive       | 9712.2            | 1063.1    | 0       | Better model               | Limited Edition: 67.05                                                              | Important confounder | ![Appendix](Logistic_Regression/Model_without_exclusive.pdf)        |


### _The main effects of the preliminary model_ 

Based on the graphs of the main effect model refinement, there appears to be a relationship between the logistic model and each predictor variable. The graph logit versus log price shows a positive relationship, suggesting that the log price variable increases the probability of the outcome of online-only sales. Similarly, the graph logit versus log value price exhibits a positive relationship, indicating that higher log value prices (price reduction) are associated with higher probabilities of online-only sales. In contrast, the graph logit versus log love reveals a negative relationship, implying that the increase in the number of users who have expressed affection or favorited a product on the Sephora platform (love) has decreased the probability of online-only sales. 

**Main effects for log price**  

```{r} 

logit <- predict(preliminar.model)  
analysisdat <- sephora[,c("limited_edition","exclusive","log_price", "log_value_price", "log_love", "online_only")]  

dat <- analysisdat[complete.cases(analysisdat),]

subset_data3 <- data.frame(dat$log_price, logit)

plot(subset_data3)

lines(lowess(subset_data3),col= 2)
``` 

![image](https://github.com/eguzmanleano30/Business_Analysis/assets/172155030/16b03686-94d3-4f2a-af9c-2f63cfcb1b32)


**Main effect for log value price**

```{r} 
subset_data4 <- data.frame(dat$log_value_price, logit)  

plot(subset_data4)  

lines(lowess(subset_data4),col= 2) 
``` 
![image](https://github.com/eguzmanleano30/Business_Analysis/assets/172155030/0ede645f-2fe6-482e-84e9-c8be5f859239)


**Main effects for log number of reviews**

```{r} 
subset_data6 <- data.frame(dat$log_love, logit)  

plot(subset_data6)  

lines(lowess(subset_data6),col= 2) 
``` 

![image](https://github.com/eguzmanleano30/Business_Analysis/assets/172155030/8503bed4-b64d-4a62-a459-bbf22597cdc0)


**Interaction effect**

The interaction analysis reveals significant relationships between predictor variables and their combined impact on online-only sales. The unique interaction that does not influence online-only sales is limited_edition vs. exclusive because it is not statistically significant. In contrast, the other interactions have demonstrated significant impacts on online-only sales. 


**Result of interaction between predictors**

| Interaction                         | Coeffic. | SE    | Z value | P-value   | Interaction effect | Output and code |
| ----------------------------------- | -------- | ----- | ------- | --------- | ------------------ | --------------- |
| limited_edition1 vs exclusive       | 0.115    | 0.174 | 0.663   | 0.507     | Not significant    | ![Appendix](Logistic_Regression/interac_limited_edition_exclusive.pdf)        |
| limited_edition1 vs log_price       | 0.546    | 0.127 | 4.295   | 1.74e-05  | significant        | ![Appendix](Logistic_Regression/interac_limited_edition_price.pdf)        |
| limited_edition1 vs log_value_price | 0.556    | 0.122 | 4.539   | 5.65e-06  | significant        | ![Appendix](Logistic_Regression/interac_limited_edition_value_price.pdf)        |
| Exclusive1 vs log_price             | 0.445    | 0.099 | 4.513   | 6.38e-06  | significant        | ![Appendix](Logistic_Regression/interac_exclusive_price.pdf)        |
| Exclusive1 vs log_value_price       | 0.447    | 0.095 | 4.709   | 2.49e-06  | significant        | ![Appendix](Logistic_Regression/interac_exclusive_value_price.pdf)        |
| log_price vs log_value_price        | 0.277    | 0.035 | 7.991   | 1.34e -15 | significant        | ![Appendix](Logistic_Regression/interac_price_value_price.pdf)        |
| log_price vs log_love               | \-0.064  | 0.029 | \-2.231 | 0.026     | significant        | ![Appendix](Logistic_Regression/interac_price_love.pdf)        |
| log_value_price vs log_love         | \-0.057  | 0.028 | \-2.035 | 0.042     | significant        | ![Appendix](Logistic_Regression/interac_value_price_love.pdf)        |


### Final model and validation. 

The final logistic regression model highlights significant predictors of online sales at Sephora. Limited edition and exclusivity negatively influence online sales, while higher log price deters purchases. Conversely, log value price positively impacts online sales, indicating that perceived value drives purchases. Interactions between limited edition and log price and exclusivity and log price further reveal slight relationships. 

Final log odd model: 

**Logg odd:**

**g_(online_only) = 3.641-1.261 limited_edition -1.612 exclusive-0.974 log_price + 0.899 log_value_price -0.553 limited_edition * log_price +0.437 exclusive * log_price**

**Statistical summary of finale log odd model**

| Variables                  | coefficient | SE    | Z value  | p.value |
| -------------------------- | ----------- | ----- | -------- | ------- |
| Intercept                  | 3.641       | 0.250 | 14.554   | 0       |
| limited_edition1           | \-1.261     | 0.502 | \-2.514  | 0.012   |
| exclusive1                 | \-1.612     | 0.369 | \-4.365  | 0       |
| log_price                  | \-0.974     | 0.243 | \-4.009  | 0       |
| log_value_price            | 0.899       | 0.238 | 3.772    | 0       |
| log_love                   | \-0.553     | 0.02  | \-27.844 | 0       |
| limited_edition1:log_price | 0.437       | 0.130 | 3.354    | 0.001   |
| exclusive1:log_price       | 0.364       | 0.101 | 3.586    | 0       |

![Statistical summary of final model with interaction effect](Logistic_Regression/final_model_with_interaction.pdf)

### Validation of the final model 

The validation of the final model reveals good results. The Hosmer-Lemeshow goodness of fit test yields a p-value of 0.1109, suggesting that the model adequately fits the data, suggesting there is no significant difference between observed and predicted outcomes. Furthermore, the high Pearson correlation coefficient of 0.965 indicates a strong correlation between observed and predicted probabilities, confirming the model's accuracy in predicting online sales for Sephora. 


-  **Hosmer and Lemeshow goodness of fit (GOF) test data:**
```{r} 
dat$online_only <- as.numeric(dat$online_only)-1

hosle_test <- hoslem.test(dat$online_only, fitted(final.model),g=10)

hosle_test
``` 

X-squared = 13.027, df = 8, p-value = 0.1109 


-   **Pearson test**
```{r} 
pr <- residuals(final.model,"pearson")

sum_pr <- sum(pr^2)

pearson <- round(1-pchisq(sum_pr, 9161),3)

pearson
``` 
Pearson correlation coefficient = 0.965 

### **_Outlier analysis_** 

The Cook's distance plot does not show extreme data points that are influential in the final model, so we do not need to drop any observation into Sephora's data.

**Plot residuals vs. fitted values with three influential point** 

```{r} 
plot(final.model, which = 4, id.n = 3)
``` 

![image](https://github.com/eguzmanleano30/Business_Analysis/assets/172155030/e2b4931f-10c0-4a2d-9332-f962f24426e0)








