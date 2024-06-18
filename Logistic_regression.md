## Logistic Regression Analysis for Online Shopping Preferences 

### Research questions: 
What factors drive customers to shop online instead of in-store at Sephora? 

### Explanation of research question 
This research question delves into the factors influencing customers’ purchase decisions between shopping online and in-store at Sephora. It seeks to identify the key product characteristics and customer preferences that lead individuals to shop online rather than visiting physical stores. 

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
















