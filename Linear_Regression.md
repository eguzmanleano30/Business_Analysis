## Linea regression Analysis of Customer Love for Sephora’s products 

### Research question 

Which factors influence the level of customer love for products sold on Sephora’s website? 

### Explanation of research question 

This research question investigates the factors contributing to the level of customer love for products available on Sephora’s website. The dependent variable, “love,” represents the number of people who love a particular product, indicating customer satisfaction and affinity towards the product. 

### Building a linear regression model for people who love products of Sephora beauty retail 

We will use a multiple linear regression model to examine what pushes customer love for Sephora's products. This approach allows us to assess how price, brand, marketing efforts, and customer reviews affect the love variable, which measures customer affection toward products. To analyze these variables together, the model will highlight the most significant influences of customer love, offering insights into practical strategies for enhancing product appeal on Sephora's platform. 


```{r}
# load data 
sephora <- read.csv("./data/cosmetic/SecondSephoraClean.csv", header = TRUE)

set.seed(123)  # Set a seed for reproducibility

# Sample 5000 rows from ds_wfood_cols_us_nona
sephoraData <- sample_n(sephora, 1000, replace = FALSE)
```

### Correlation Analysis: The log love variable in Sephora data 

Analyzing the log love correlations in the Sephora dataset highlights a few trends: 

-  **Strong Positive Correlation with log number of reviews:** A robust positive correlation (0.84) with log number of reviews indicates that products with more reviews are generally more loved, suggesting the importance of customer feedback in driving affection towards products. 

-  **Negative Correlation with Online Only:** The negative correlation (-0.38) with online-only suggests that products exclusively sold online are less loved, possibly reflecting a preference for in-store experiences. 

-  **Slight Negative Correlation with log price:** log love shows a slight negative correlation with both log_price (-0.18) and log_value_price (-0.20), indicating that higher-priced products may be less accessible or have higher expectations that are not always met. 

 -  **Positive Correlation with rating:** A moderate positive correlation (0.34) with rating suggests that better-rated products are more loved, highlighting the value of product quality and satisfaction. 

**Correlation Matrix of Sephora data with all predictors**  

```{r}
# Selecting all predictors
totalVariable <- select(sephoraData, "log_love", "log_number_of_reviews", "log_price",
                   "log_value_price", "rating", "online_only", "exclusive", "limited_edition", "limited_time_offer")

# argument lab = TRUE
ggcorrplot(round(cor(totalVariable), 3),
           hc.order = TRUE,
           type = "lower",
           lab = TRUE)

```

![image](https://github.com/eguzmanleano30/Business_Analysis/assets/172155030/905c9159-638f-4f66-be8d-82f14f22bce6)

 
**Log love response correlation with all predictors** 

| Variable 1             | Variable 2             | Correlation |
| --------------------- | --------------------- | ----------- |
|   | Log price             | \-0.18      |
|   | Log value price       | \-0.2       |
| **Log love**  | Log number of reviews | 0.84        |
|   | rating                | 0.34        |
|   | Online only sales     | \-0.38      |
|   | Exclusive             | 0.12        |
|   | Limited edition       | \-0.11      |


### L.I.N.E.  assumption diagnostic for numerical variables 

### Diagnostic of linearity and independence assumptions 

The linearity assumption test results for multiple linear regression of Sephora data suggest no evident pattern observed in the residuals versus predictors and residuals versus fitted values plots for the log value price, log price, and rating predictors, indicating no violation of linearity assumptions. However, for the log number of reviews predictor, a clear U-shaped pattern is observable in both plots, indicating a violation of the linearity assumption. 

On the other hand, examining the independence assumption revealed consistent outcomes across predictors. Each predictor, including log value price, log price, log number of reviews, and rating, exhibited random cloud patterns in the residuals versus order plots. This randomness suggests no systematic relationship between residuals and the order of observations. Therefore, it’s indicated no violation of the independence assumption for any of the predictors. 



|   | Linearity assumption  |   |   | Independence assumption  |   |   |  
| --------------------- | --------------------- | -------------------------- | ---------------- | ------------------ | ------------ | --------------- |
|  **<br>Predictor**        | **Residual vs predictor** | **Residual vs. fitted values** | **Conclusion**       | **Residual vs. order** | **Conclusion**   | **Output and code** |
| Log value price       | No pattern            | No pattern                 | No <br>Violation | Random cloud       | No violation | ![Appendix](Linear_Regression/Value_price_lineari_Independ.pdf)        |
| Log price             | No pattern            | No pattern                 | No <br>Violation | Random cloud       | No violation | ![Appendix](Linear_Regression/Price_lineari_Independ.pdf)        |
| Log number of reviews | U pattern             | U pattern                  | Violation        | Random cloud       | No violation | ![Appendix](Linear_Regression/number_review_lineari_Independ.pdf)        |
| Rating                | No pattern            | No pattern                 | No <br>Violation | Random cloud       | No violation | ![Appendix](Linear_Regression/Rating_lineari_Independ.pdf)        |


### Diagnostics of normality assumptions for predictors 

Based on the analysis of the normality assumption – as illustrated in the following table -- for the numerical variables in Sephora data, it can be concluded that most predictors satisfy the normality assumption. Indeed, log value price, and log price rating variables exhibit straight diagonal lines in their QQ plots, indicating conformity to a normal distribution. Correspondingly, their histograms display a normal distribution pattern, with some outliers on the left side of the boxplot. The Shapiro-Wilks tests for these predictors failed to reject the null hypothesis, with p-values of 0.243, 0.224, and 0.204, confirming that errors are normally distributed. Therefore, there is no violation of the normality assumption. However, for the log number of reviews, the QQ plot shows an outlier down the line and slight skewness to the right in the histogram, with some outliers mainly on the right side of the boxplot. The Shapiro-Wilks test rejected the null hypothesis with a very low p-value, indicating that errors are not normally distributed. Therefore, this is a violation of the assumption of normality.


|                        | Normality assumption    |                               |                                      |                                                                  |                |
|------------------------|-------------------------|-------------------------------|--------------------------------------|------------------------------------------------------------------|----------------|
| Predictor              | QQ plot                 | Histogram                     | Boxplot                              | Shapiro-Wilks test                                               | Conclusion     |
| Log value price        | straight diagonal line  | Norm. Ditribu.                | some outliers left                   | Fail reject Ho  p-value: 0.243  Errors are normally distributed  | No. violation  |
| Log price              | straight diagonal line  | Norm. Ditribu.                | some outliers left                   | Fail reject Ho  p-value: 0.224  Errors are normally distributed  | No. violation  |
| Log number of reviews  | Outlier down line       | slight skewness to the right  | some outliers right                  | reject Ho  p-value=1.58e-9  Errors are NOT normally distributed  | violation      |
| Rating                 | straight diagonal line  | Norm. Ditribu.                | some outliers to the left and right  | Fail reject Hop-value: 0.204  Errors are normally distributed    | No. violation  |
















