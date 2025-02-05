# Best Selling Products
Assuming that total_sales column represented the amount of profit of off each unique product, I summed up the total_sales columns grouped by product number. Sorting this in descending order gave me the top  3 highest sold products.
The products and their total sales are as follows.

Smiths Crinkle Chips Salt & Vinegar 330g  :  40352.0 

Dorito Corn Chp     Supreme 380g  :  36367.6 

Smiths Crnkle Chip  Orgnl Big Bag 380g  :  34804.200000000004 

# Characteristics of Loyal customers
Since the Transaction and customer data was given in two different CSVs, I merged the two files using LYLTY_CARD_NBR as the key. 
Two find the most important characteristics for loyal customers, a groupby operation on LIFESTAGE and PREMIUM_CUSTOMER was performed, taking sum of the TOT_SALES for each group
However, this still gave us two attributes with different degrees of freedoms. To find the whether LIFESTAGE or PREMIUM_CUSTOMER explained more variance in the TOT_SALES value, an ANOVA test was performed on the data.

## LIFESTAGE
The ANOVA table for LIFESTAGE was as follows:

| Source         | sum_sq        | df  | F        | PR(>F)   |
|----------------|---------------|-----|----------|----------|
| C(LIFESTAGE)   | 3.042608e+10  | 6.0 | 4.190129 | 0.012769 |
| Residual       | 1.694320e+10  | 14.0| NaN      | NaN      |

given a large F value and a P value less than 0.05, it was conclusive that LIFESTAGE had a statistically significant effect on TOT_SALES.

## PREMIUM_CUSTOMER
The ANOVA table for PREMIUM_CUSTOMER was as follows:

| Source             | sum_sq        | df  | F        | PR(>F)   |
|--------------------|---------------|-----|----------|----------|
| C(PREMIUM_CUSTOMER)| 4.439069e+09  | 2.0 | 0.930618 | 0.412473 |
| Residual           | 4.293020e+10  | 18.0| NaN      | NaN      |

Given the high P-value, we can conclude that PREMIUM_CUSTOMER attribute had no significant effect on TOT_SALES.

# Conclusion
The top 3 highest sales contributions were:

| LIFESTAGE              | PREMIUM_CUSTOMER | TOT_SALES  |
|------------------------|------------------|------------|
| OLDER FAMILIES         | Budget           | 168363.25  |
| YOUNG SINGLES/COUPLES  | Mainstream       | 157621.60  |
| RETIREES               | Mainstream       | 155677.05  |

But the 3 largest mean sales across all types of cards were:

| LIFESTAGE              | TOT_SALES  |
|------------------------|------------|
| OLDER SINGLES/COUPLES  | 134142.25  |
| RETIREES               | 122156.96  |
| OLDER FAMILIES         | 117922.39  |

So we can conclude that LIFESTAGE of the customers is more important compared to the types of cards they used. 
