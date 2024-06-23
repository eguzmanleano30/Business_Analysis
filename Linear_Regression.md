## Linea regression Analysis of Customer Love for Sephora’s products 

### Research question 

Which factors influence the level of customer love for products sold on Sephora’s website? 

### Explanation of research question 

This research question investigates the factors contributing to the level of customer love for products available on Sephora’s website. The dependent variable, “love,” represents the number of people who love a particular product, indicating customer satisfaction and affinity towards the product. 

### Building a linear regression model for people who love products of Sephora beauty retail 

We will use a multiple linear regression model to examine what pushes customer love for Sephora's products. This approach allows us to assess how price, brand, marketing efforts, and customer reviews affect the love variable, which measures customer affection toward products. To analyze these variables together, the model will highlight the most significant influences of customer love, offering insights into practical strategies for enhancing product appeal on Sephora's platform. 

**Getting a sample of Sephora's data**
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

```{r}
# Calculate the correlation matrix
correlation_matrix <- cor(sephoraNum)

# Get the row and column indices for the lower triangle
lower_triangle_indices <- which(lower.tri(correlation_matrix), arr.ind = TRUE)

# Extract the lower triangle of the correlation matrix along with variable names
lower_triangle <- correlation_matrix[lower_triangle_indices]

# Get the variable names corresponding to the lower triangle
row_names <- rownames(correlation_matrix)[lower_triangle_indices[, 1]]
col_names <- colnames(correlation_matrix)[lower_triangle_indices[, 2]]

# Create a data frame to display the lower triangle with variable names
lower_triangle_df <- data.frame(Variable1 = row_names,
                                Variable2 = col_names,
                                Correlation = lower_triangle)

# Sort the lower triangle data frame by variable 1 in ascending order
sorted_lower_triangle_df <- lower_triangle_df[order(lower_triangle_df$Variable2), ]

# table the correlation
kbl(sorted_lower_triangle_df) %>%
kable_classic_2(full_width = F)
```



 
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

**Results of diagnostics of linearity and independence assumptions**
|   | Linearity assumption  |   |   | Independence assumption  |   |   |  
| --------------------- | --------------------- | -------------------------- | ---------------- | ------------------ | ------------ | --------------- |
|  **<br>Predictor**        | **Residual vs predictor** | **Residual vs. fitted values** | **Conclusion**       | **Residual vs. order** | **Conclusion**   | **Output and code** |
| Log value price       | No pattern            | No pattern                 | No <br>Violation | Random cloud       | No violation | ![Appendix](Linear_Regression/Value_price_lineari_Independ.pdf)        |
| Log price             | No pattern            | No pattern                 | No <br>Violation | Random cloud       | No violation | ![Appendix](Linear_Regression/Price_lineari_Independ.pdf)        |
| Log number of reviews | U pattern             | U pattern                  | Violation        | Random cloud       | No violation | ![Appendix](Linear_Regression/number_review_lineari_Independ.pdf)        |
| Rating                | No pattern            | No pattern                 | No <br>Violation | Random cloud       | No violation | ![Appendix](Linear_Regression/Rating_lineari_Independ.pdf)        |


### Diagnostics of normality assumptions for predictors 

Based on the analysis of the normality assumption – as illustrated in the following table -- for the numerical variables in Sephora data, it can be concluded that most predictors satisfy the normality assumption. Indeed, log value price, and log price rating variables exhibit straight diagonal lines in their QQ plots, indicating conformity to a normal distribution. Correspondingly, their histograms display a normal distribution pattern, with some outliers on the left side of the boxplot. The Shapiro-Wilks tests for these predictors failed to reject the null hypothesis, with p-values of 0.243, 0.224, and 0.204, confirming that errors are normally distributed. Therefore, there is no violation of the normality assumption. However, for the log number of reviews, the QQ plot shows an outlier down the line and slight skewness to the right in the histogram, with some outliers mainly on the right side of the boxplot. The Shapiro-Wilks test rejected the null hypothesis with a very low p-value, indicating that errors are not normally distributed. Therefore, this is a violation of the assumption of normality.

**Result of diagnostics of normality assumption**

| Predictor              | QQ plot                 | Histogram                     | Boxplot                              | Shapiro-Wilks test                                               | Conclusion     | Output and code |
|------------------------|-------------------------|-------------------------------|--------------------------------------|------------------------------------------------------------------|----------------|-----------------|
| Log value price        | straight diagonal line  | Norm. Ditribu.                | some outliers left                   | Fail reject Ho  p-value: 0.243  Errors are normally distributed  | No. violation  | ![Appendix](Linear_Regression/Normality_value_price.pdf)        |
| Log price              | straight diagonal line  | Norm. Ditribu.                | some outliers left                   | Fail reject Ho  p-value: 0.224  Errors are normally distributed  | No. violation  | ![Appendix](Linear_Regression/Normality_price.pdf)        |
| Log number of reviews  | Outlier down line       | slight skewness to the right  | some outliers right                  | reject Ho  p-value=1.58e-9  Errors are NOT normally distributed  | violation      | ![Appendix](Linear_Regression/Normality_numb_of_review.pdf)        |
| Rating                 | straight diagonal line  | Norm. Ditribu.                | some outliers to the left and right  | Fail reject Hop-value: 0.204  Errors are normally distributed    | No. violation  | ![Appendix](Linear_Regression/Normality_rating.pdf)        |



### Diagnostics of equal variance assumption for predictors 

The equal variance assumption for the numerical variables – as shown in the following table -- in the Sephora dataset presents mixed results. The scatter plots show random clouds for comparisons against predictors and residuals for log value price. Levene’s Test results in a failure to reject the null hypothesis with high p-values (0.789 and 0.457), indicating constant error variance and no assumption violation. However, the assumption encounters issues with the log number of reviews and ratings. Both variables show U-shaped patterns in their residual plots, suggesting non-constant variance across values. This observation is confirmed by Levene’s Test, which rejects the null hypothesis for both (p-values of 0.002 and 5.379e-06, respectively), indicating a clear violation of the equal variance assumption for these predictors. 

**Result of diagnostic of equal variance assumption**

|   Predictor            | Log love vs Predictor  | Residual vs predictor  | Levene’s Test                                                | Conclusion    | Output and code |
|------------------------|------------------------|------------------------|--------------------------------------------------------------|---------------|-----------------|
| Log value price        | Random cloud           | Random cloud           | Fail reject Ho  P-value: 0.789  Error variance is constant   | No violation  | ![Appendix](Linear_Regression/equal_variance_value_price.pdf)        |
| Log price        | Random cloud           | Random cloud           | Fail reject Ho  P-value: 0.457  Error variance is constant   | No violation  | ![Appendix](Linear_Regression/equal_variance_price.pdf)        |
| Log number of reviews  | Random cloud           | U shape                | reject Ho  P-value: 0.002  Error variance is constant        | Violation     | ![Appendix](Linear_Regression/equal_variance_numb_of_review.pdf)        |
| Rating                 | U shape                | U shape                | reject HoP-value: 5.379e-06  Error variance is not constant  | Violation     | ![Appendix](Linear_Regression/equal_variance_rating.pdf)        |


### Analysis of categorical variables 

The t-test analysis for the influence of categorical variables on Sephora data demonstrates significant results for most variables, suggesting they should not be excluded from the linear regression model. The predictors "Online only," "Exclusive," and "Limited edition" give t-values (12.97, 3.38, and 3.52, respectively) that significantly exceed the critical value of 1.65. Their p-values indicate a solid rejection of the null hypothesis (all p-values are 0). This suggests that these variables have a statistically significant impact on the dependent variable and should be included in the model. Contrarily, the "Limited time offer" variable, with a t-value of 0.38 and a p-value of 0.703, fails to reject the null hypothesis, suggesting it does not significantly affect the dependent variable. Therefore, it can be excluded from further modeling. 

**T-test result for categorical variables**

| Predictor           | T*    | T    | p-value  | T-test                                 | Conclusion           | Output and code |
|---------------------|-------|------|----------|----------------------------------------|----------------------|-----------------|
| Online only         | 12.97 | 1.65 | 0        | Reject Ho  Statistic significant       | No exclude variable  | ![Appendix](Linear_Regression/Analisis_of_online_only_variable.pdf)        |
| exclusive           | 3.38  | 1.65 | 0        | Reject Ho  Statistic significant       | No exclude variable  | ![Appendix](Linear_Regression/Analisis_of_exclusive_variable.pdf)        |
| Limited edition     | 352   | 1.65 | 0        | Reject Ho  Statistic significant       | No exclude variable  | ![Appendix](Linear_Regression/Analisis_of_limited_edition_variable.pdf)        |
| Limited time offer  | 0.38  | 1.65 | 0.703    | Fail Reject Ho  Statistic significant  | exclude variable     | ![Appendix](Linear_Regression/Analisis_of_limited_time_offer.pdf)        |


### Predictors selected to build linear regression model

The selection of six predictors for the linear regression model analyzing log love in Sephora data —rating, number of reviews, log price, log value price, exclusive, and limited edition— is based on their statistical significance and relevance, as supported by LINE assumption analysis for numerical variables, and the t-test for categorical variables. 


```{r}
# Select numerical variables 
variablesSelecting <- select(sephoraData, "rating", "log_number_of_reviews", "log_price", "log_value_price", "exclusive", "limited_edition","log_love")


# Create pairs plot using ggpairs
ggpairs(variablesSelecting)
```
**Correlation with all predictors selected**

![image](https://github.com/eguzmanleano30/Business_Analysis/assets/172155030/78d90195-bca6-43ee-95c8-0acdb2f05371)


**Preliminary model:** 

**log(love)** = 5.871+ 0.088*rating + 0.684*log(number_of_reviews) - 0.806*Log(price) +   0.659*Log(value_price) +0.309*exclusive + 0.283*limited_edition 


**Summary of preliminary model**

```{r}
# Fit linear regression model
preli_model2 <- lm(log_love ~ rating + log_number_of_reviews + log_price + log_value_price + factor(exclusive) + factor(limited_edition), data = sephoraData)

sum_preliminar.model <- tidy(preli_model2)

kbl(sum_preliminar.model) %>%
kable_classic_2(full_width = F)
```

|                        | Coefficient  | SE     | z       | p.value  |
|------------------------|--------------|--------|---------|----------|
| (Intercept)            | 5.871        | 0.182  | 32.310  | 0.000    |
| rating                 | 0.088        | 0.026  | 3.361   | 0.001    |
| log_number_of_reviews  | 0.684        | 0.015  | 45.563  | 0.000    |
| log_price              | -0.806       | 0.289  | -2.793  | 0.005    |
| log_value_price        | 0.659        | 0.284  | 2.320   | 0.021    |
| exclusive              | 0.309        | 0.061  | 5.102   | 0.000    |
| limited_edition        | 0.283        | 0.103  | 2.747   | 0.006    |


### Model refinement and selection 

The analysis of the Sephora data using linear regression explored various models to determine which factors most significantly influence customer affection, as measured by the love variable. Two criteria, Ra^2 (adjusted R-squared) and Cp (Mallow's Cp), were employed to assess model performance. Among the models tested, model six was identified as optimal according to both criteria. This model incorporates six predictors: rating, log number of reviews, log price, log value price, exclusivity, and limited edition. It achieved an adjusted R-squared of 0.730 and a Cp value of 7, suggesting it has substantial explanatory power while effectively balancing complexity and fit. This comprehensive approach ensures that the selected model provides a robust framework for understanding the dynamics of customer preferences on Sephora’s platform.

**Result of examination of all best models using Ra2 criterion**  

```{r}
# Create a design matrix with variables VA1, VA7, and VA10
x <- sephoraData[, c("rating", "log_number_of_reviews", "log_price", "log_value_price", "exclusive", "limited_edition")]

# Perform stepwise variable selection using leaps
Ra2 <- leaps(x = x, y = sephoraData$log_love, method = "adjr2", nbest = 1)

Ra2_table <- data.frame(Ra2$which, num_in_model = Ra2$size - 1, 
                        p = Ra2$size,
                        adjr2 = Ra2$adjr2) %>% 
  arrange(desc(adjr2))

kbl(Ra2_table) %>%
kable_classic_2(full_width = F)
```


| Num of model  | X1     | X2    | X3     | X4     | X5     | X6     | Number of predictors  | adjr2  |
|---------------|--------|-------|--------|--------|--------|--------|-----------------------|--------|
| 6             | TRUE   | TRUE  | TRUE   | TRUE   | TRUE   | TRUE   | 7                     | 0.730  |
| 5             | TRUE   | TRUE  | TRUE   | FALSE  | TRUE   | TRUE   | 6                     | 0.729  |
| 4             | FALSE  | TRUE  | TRUE   | FALSE  | TRUE   | TRUE   | 5                     | 0.726  |
| 3             | FALSE  | TRUE  | FALSE  | FALSE  | TRUE   | TRUE   | 4                     | 0.723  |
| 2             | FALSE  | TRUE  | FALSE  | FALSE  | TRUE   | FALSE  | 3                     | 0.72   |
| 1             | FALSE  | TRUE  | FALSE  | FALSE  | FALSE  | FALSE  | 2                     | 0.707  |



X^2^


$R^2_a$






