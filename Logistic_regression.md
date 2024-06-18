## Logistic Regression Analysis for Online Shopping Preferences 

### Research questions: 
What factors drive customers to shop online instead of in-store at Sephora? 

### Explanation of research question 
This research question delves into the factors influencing customers’ purchase decisions between shopping online and in-store at Sephora. It seeks to identify the key product characteristics and customer preferences that lead individuals to shop online rather than visiting physical stores. 

### Building a logistic regression model for products sold online only
To build a logistic regression model, we will incorporate all independent variables. The aim is to predict the likelihood of a product being exclusively sold online on Sephora’s website. This model will enable Sephora to optimize its product assortment, marketing strategies, and distribution channels to maximize online sales and enhance overall profitability. Additionally, insights gained from the model can inform strategic decision-making and help Sephora stay competitive in the rapidly evolving e-commerce landscape. 

### _Univariable analysis_
The following table shows the univariable logistic regression analysis on the Sephora web platform dataset, revealing potential associations between various independent variables and online-only sales. Significant factors such as rating, limited edition, exclusive, log price, log value price, and log love may influence online sales, as is evident from their Wald test p-values below 0.25. In contrast, category, limited edition offers, and MarketingFlags show no significant associations with online-only sales.



**Univariable results**
| Indepen. Variable     | Coeffic. (B1) | Standard Error | Wald Test | P-value | conclusion                                        | Output and code |
| --------------------- | ------------- | -------------- | --------- | ------- | ------------------------------------------------- | --------------- |
| Category              | 0             | 1.782 e3       | 0         | 1       | No significant association with online-only sales | ![Appendix](        |
| Rating                | \- 0.083      | 0.0463         | \-1.801   | 0.0717  | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_Rating.pdf)        |
| limited edition       | 0.702         | 0.077          | 9.144     | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_limited_edition.pdf)        |
| Limited Edition Offer | \-10.384      | 113.719        | \-0.091   | 0.9275  | No significant association with online-only sales | ![Appendix](        |
| Exclusive             | \-0.414       | 0.06026        | \-6.871   | 0       | Potential significance for online-only sales      | ![Appendix](Logistic_Regression/Univaria_Analis_Exclusive.pdf)        |
| MarketingFlag         | 19.54         | 156.68         | \-0.091   | 0.9     | No significant association with online-only sales | ![Appendix](        |
| Log Price             | 0.299         | 0.0357         | 8.385     | 0       | Potential significance for online-only sales      | ![Appendix](        |
| Log Value Price       | 0.334         | 0.03506        | 9.544     | 0       | Potential significance for online-only sales      | ![Appendix](        |
| Log Love              | \-0.574       | 0.0193         | \-29.68   | 0       | Potential significance for online-only sales      | ![Appendix](        |



























