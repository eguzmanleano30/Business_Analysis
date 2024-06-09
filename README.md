# Exploration Data Analsis of Sephora website

Sephora data incorporates varied variables, capturing product characteristics and customer interactions on Sephora's website. Categorical variables include product brand, category, size, marketing flags, and product details, while numerical variables comprise product ID, rating, number of reviews, customer affection (love), and price-related metrics. Before analysis, the dataset undergoes meticulous cleaning to handle missing values, rectify data errors, and ensure uniformity across categories. The variables irrelevant to our research questions will be eliminated to streamline the analysis. 

## Understand The Dataset

Sephora's dataset – with 21 variables and 91,658 observations – provides essential insights into its product offerings online. This information discloses valuable insights into Sephora's product lineup, customer preferences, and marketing strategies. Sephora's variables are grouped into four types of variables:

```{r}
dim(sephora)

skim(sephora)
```
[ouput](https://github.com/eguzmanleano30/Exploration_Data_Analisis/blob/main/EDA/ExplorationData.png)
-   **Informative Variables:** These include essential product details, such as their IDs, brands, names, sizes, URLs, available options (like colors and sizes), product details, usage instructions, ingredients, and marketing flags. 

-   **Binary Variables:** These variables indicate specific product attributes or conditions using binary values, such as whether the product is sold exclusively online, is exclusive to Sephora's website, is a limited-edition item, or has a limited-time offer

-   **Categorical Variables:** This category encompasses the types or categories to which products belong on the Sephora website, providing a structured way to organize and classify products.

-   **Numerical Variables:** These variables quantify different aspects of the products, including their ratings, the number of reviews they have received, the number of customers who have shown interest or "love" for the products, their prices, and their value prices (applicable for discounted products).

## Clean the Data 

### _Addressing Inconsistent Rows._  

During the data examination process, it was noted that 58 rows exhibited inconsistencies or errors. These rows were excluded from the data to uphold data integrity and reliability. 

### _Addressing Missing Values._ 

The Sephora dataset reveals 5082 significant missing values in two specific variables (rating and MarketingFlags_content), highlighting potential gaps in the dataset's completeness and accuracy. These missing entries underline the importance of addressing data integrity and the need for careful preprocessing before any analytical or predictive modeling efforts. 

**a)  Missing Values in rating:** The rating variable has 371 missing values. Given the importance of the rating variable in our analysis, we decided to retain these missing values. Imputation methods were not applied due to the relatively small proportion of missing values. 

**b)  Exclusion of MarketingFlags_content:** The MarketingFlags_content variable had many missing values, with 4711 observations missing. Considering its limited relevance to our analysis objectives and the high proportion of missing values, we excluded this variable from the entire dataset. 




