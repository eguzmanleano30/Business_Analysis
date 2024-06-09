# Exploration Data Analsis of Sephora website

Sephora data incorporates varied variables, capturing product characteristics and customer interactions on Sephora's website. Categorical variables include product brand, category, size, marketing flags, and product details, while numerical variables comprise product ID, rating, number of reviews, customer affection (love), and price-related metrics. Before analysis, the dataset undergoes meticulous cleaning to handle missing values, rectify data errors, and ensure uniformity across categories. The variables irrelevant to our research questions will be eliminated to streamline the analysis. 

## Understand The Dataset

Sephora's dataset – with 21 variables and 91,658 observations – provides essential insights into its product offerings online. This information discloses valuable insights into Sephora's product lineup, customer preferences, and marketing strategies. Sephora's variables are grouped into four types of variables:

-   **Informative Variables:** These include essential product details, such as their IDs, brands, names, sizes, URLs, available options (like colors and sizes), product details, usage instructions, ingredients, and marketing flags. 

-   **Binary Variables:** These variables indicate specific product attributes or conditions using binary values, such as whether the product is sold exclusively online, is exclusive to Sephora's website, is a limited-edition item, or has a limited-time offer

-   **Categorical Variables:** This category encompasses the types or categories to which products belong on the Sephora website, providing a structured way to organize and classify products.

-   **Numerical Variables:** These variables quantify different aspects of the products, including their ratings, the number of reviews they have received, the number of customers who have shown interest or "love" for the products, their prices, and their value prices (applicable for discounted products).

```{r}
dim(sephora)

skim(sephora)
```
[ouput](https://github.com/eguzmanleano30/Exploration_Data_Analisis/blob/main/EDA/ExplorationData.png)

## Clean the Data 

### _Addressing Inconsistent Rows._  

During the data examination process, it was noted that 58 rows exhibited inconsistencies or errors. These rows were excluded from the data to uphold data integrity and reliability. 

### _Addressing Missing Values._ 

The Sephora dataset reveals 5082 significant missing values in two specific variables (rating and MarketingFlags_content), highlighting potential gaps in the dataset's completeness and accuracy. These missing entries underline the importance of addressing data integrity and the need for careful preprocessing before any analytical or predictive modeling efforts. 

**a)  Missing Values in rating:** The rating variable has 371 missing values. Given the importance of the rating variable in our analysis, we decided to retain these missing values. Imputation methods were not applied due to the relatively small proportion of missing values. 

**b)  Exclusion of MarketingFlags_content:** The MarketingFlags_content variable had many missing values, with 4711 observations missing. Considering its limited relevance to our analysis objectives and the high proportion of missing values, we excluded this variable from the entire dataset. 

```{r}
md.pattern(sephora[c("category", "number_of_reviews", "love", "price","value_price", "MarketingFlags", "online_only", "exclusive", "limited_edition", "limited_time_offer", "log_love", "log_price", "log_value_price", "log_number_of_reviews", "rating", "MarketingFlags_content")], rot = 45)
```

**Pattern of missingness between variables in the Sephora data set**
![MissingValues](https://github.com/eguzmanleano30/Exploration_Data_Analisis/assets/172155030/5a49fd44-792e-403f-bb60-360ed5804c0d)


### Exploration of numerical variables.  

The following table shows the result of the exploration analysis of numerical variables in the Sephora dataset. It reveals consistent right-skewed distributions across the “love,” “number of reviews,” “price,” and “value price” variables, with skewness ranging from 3.13 to 9.75 and kurtosis from 17.56 to 162.13. Visual examination through QQ plots, box plots, and histograms confirms the presence of outliers, particularly to the left. Appendices B, C, D, and E provide detailed exploration results for each variable mentioned. Given the pronounced skewness and outliers, logarithmic transformation is recommended to normalize the data and improve its distributional characteristics, facilitating a more robust analysis. The appendixes from Appendix B to Appendix E illustrates the exploration analysis in more details for each variable. 





| Variable          | Skewness | Kurtosis | QQ Plot      | Box Plot                  | Histogram           | Transfor. suggestion | 
| ----------------- | -------- | -------- | ------------ | ------------------------- | ------------------- | -------------------- |
| love              | 9.63     | 162.13   | Inverted "L” | Many outliers to the left | Skewed to the right | Logarithmic          | [love](EDA/PDF/exploration_love.pdf)
| Number of reviews | 9.75     | 135.21   | Inverted "L” | Many outliers to the left | Skewed to the right | Logarithmic          |
| price             | 3.16     | 17.723   | Inverted "L” | Many outliers to the left | Skewed to the right | Logarithmic          |
| Value price       | 3.13     | 17.56    | Inverted "L” | Many outliers to the left | Skewed to the right | Logarithmic          |



[9.63](Skewness:-9.63)


 
Exploration of “love” variable 

The histogram and density plots of the love variable exhibit a pronounced right skewness. The kurtosis value of 162.13 indicates heavy-tailedness. The skewness value is 9.63, suggesting a substantial deviation from the normal distribution. The QQ plot displays an inverted "L" shape, indicating deviations from normality, while the boxplot showcases a thin box with numerous outliers to the left. A logarithmic transformation could normalize the distribution, making the data more suitable for analysis. 

```{r}
# Skewness and kurtosis
skewness(sephora$love)

kurtosis(sephora$love)
```


Skewness: 9.63       Kurtosis: 162.13 

 ```{r}
# Exploration love varaible

# Set up the plotting layout
par(mfrow = c(1, 2))

# Plot histogram and density
hist(sephora$love, xlab = "people who love the product", main = "Histogram of love variable")

plot(density(sephora$love), main = "Density (x=love)")

```
Histogram and density for love variable. 

 ![Histogram_density_love](https://github.com/eguzmanleano30/Exploration_Data_Analisis/assets/172155030/7747b594-a7c4-4059-ac68-ed20cabeba1f)


 

 
QQ and box plots for love variable. 


 

 
Exploration of “price” variable 

The 'price' variable exhibits a right-skewed distribution, as evident from its histogram and density plots. The skewness of 3.156 and a kurtosis of 17.723 indicate a heavy-tailed distribution. The QQ plot and boxplot confirm this skewness, showing an inverted "L" shape and many outliers to the left. A logarithmic transformation could normalize the distribution, making the data more suitable for analysis. 

     Skewness: 3.15       Kurtosis: 17.723 

 
Histogram and density for price variable. 

 

  

 

 
QQ and box plots for price variable. 


 

 
Exploration of the “value price” variable 

The 'value_price' or discounted price shows a right-skewed distribution, as highlighted by its histogram and density plots, with a skewness of 3.13 and a kurtosis of 17.56. These statistics suggest a pronounced tail to the right. The QQ plot presents an inverted "L" shape, and the boxplot reveals a thin box with numerous outliers to the left. Given these observations, a logarithmic transformation could help normalize the data distribution. 

     Skewness: 3.13       Kurtosis: 17.56 

 
Histogram and density for value price variable. 

 

 

 

 

 
QQ and box plots for value variable 

 

 

 

 
Exploration of the “Number of reviews” variable 

The 'number of reviews' variable shows a strong right skew, with a skewness of 9.75 and kurtosis of 135.21, indicating most products have few reviews, while a small number have many. The data's distribution suggests a logarithmic transformation could normalize it, improving analytical outcomes. 
    Skewness: 9.75       Kurtosis: 135.21 

 
Histogram and density for value price variable 

 

 

 
QQ and box plots for value variable 

 

 

 












