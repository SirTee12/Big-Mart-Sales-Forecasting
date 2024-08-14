# Big mart Sales Forecasting
Sales forecasting plays an important role in business development. Regardless of the size of a business or the number of salespeople, accurate sales forecasting can have a significant impact on all aspects of sales management, including planning, budgeting, and determining sales. In most densely populated cities, where the number of stores is growing, sound sales forecasting helps stores develop scientific and effective sales strategies to increase store revenues and reduce unnecessary losses.

# Data and Methods
The data scientists at Big Mart have collected 2013 sales data for 1559 products across 10 stores in different cities. Also, certain attributes of each product and store have been defined. The aim is to build a predictive model and predict the sales of each product at a particular outlet. Using this model, Big Mart will try to understand the properties of products and outlets which play a key role in increasing sales.

Please note that the data may have missing values as some stores might not report all the data due to technical glitches. Hence, it will be required to treat them accordingly.

# Data Cleaning and Exploration
The data has 12 columns with 8523 entries. The following could be deducted form the initial exploration
+ All the columns have no missing values except the **Item_Weight* and **Outlet_Size** columns both having 17.16% and 28.27% of their values missing respectively. 
+ The store sells 1559 unique items or products. This is too many to be useful, we need to see how we can categorise them into a smaller number of groups 
+ in the Item_Fat_Content column, there appears to be inconsistencies in the data as **Low Fat** is also represented as *LF* or **low fat** in some rows. We can also see **Regular** being represented as **reg** in some rows. We will use **Low Fat** and **Regular** as replacement for these to ensure data quality.
+ The min value of Item_Visibility is 0, but this can not be as every item must have some visibility.
+ There are only 16 Item_Type.
+ There are 10 stores.

# Exploratory data Analysis
## Univariate Analysis
Observations:
+ We observe that the item weight range from 5 Kg to 23 Kg.
+ Item_Visibility and Item_Outlet-Sales feature is right skewed. We can may be try to do a transformation in order to obtain a normal ou Gaussian distribution
+ There are more products in the range of 100 MRP - 180 MRP in the Item_MRP feature
+ We can observe that a lots of stores have been established in the years 1985, 1998 etc... and there was no store establishment between 1989 and 1996.
+ It can be aslo be see that Item Weight and Item MRP follows a normal distribution aproximately.
 + majority of the outlet have been in existence betweeen 14 years and above
 + There are outliers in the Item_Visibility and Item_Outlet_Sales column. We will have to remove some outliers
 + Vlaues in the Item_Weight and Item_MRP column seems to be evenly distributed as confirmed before.

## Bivariate Analysis
+ All sales Outlet had similar buying pattern as the proportion of each item type category is almost the same.
+ As expected, food items are the commonly purchased across all outlet given the fact that it one of the most important need of the human followed by non-consumables and then drinks
+ Every sales Outlet have all item categories
+ OUT027 made the most sales. The outlet is of medium size surpassing OUT013 whose size is much larger. This migt be due to the fact that it might be supermarket or be located in top tier cities
+ OUT010 and OUT019 had the lowest amount of sales as they are grocery stores with not so many customers comapared to other outlets

having a large oulet size doesnt mean you make more sales because you might out of stock on essential commodities at certain points when demands.
In conclusion, while having a larger store may have the potential to boost sales, this potential must be realized via robust product offers, successful marketing, first-rate customer service, and smooth operations.

Well this is a big surprise seeing tier 3 outlets having more sales than other outlet in tier 1 and 2. One would expect more sales in tier 1 and 2 due to economic strength, population, standard of livivng etc but that isn't the case here. there various reasons why outlets in tier 1 cities would make lower sales compared to other tiers

+ Market Penetration and Targeting: Companies frequently putting more focus their marketing and distribution efforts on Tier 1 and Tier 2 cities, assuming these areas have greater purchasing power. However, this approach can sometimes lead to excess inventory or a disconnect with local consumer preferences, which may result in lower-than-expected sales. On the other hand, adopting tailored marketing strategies that resonate with the unique needs and tastes of consumers in Tier 3 and smaller cities can lead to a stronger market fit and improved sales outcomes in those regions.
+ Consumer Behavior and Preferences: Customers in Tier 1 and Tier 2 cities may be less inclined to buy particular items since they have different lifestyle choices and access to a greater variety of options. For example, individuals could prefer digital services to tangible things, or the other way around. Tier 3 and smaller cities, on the other hand, could have cultural or economic characteristics that are more in line with the goods or services being provided, leading to better acceptance and sales.
+ Economic Shifts and Development: Tier 1 and 2 cities may experience economic fluctuations that impact consumer spending power, such as rising costs or economic downturns. Conversely, Tier 3 and lower cities might be experiencing economic growth or development, increasing disposable income and leading to higher sales.

# Machine Learning Development
Another possible solution is to use machine learning algorithms to create predictive models based on sales data, to identify the market characteristics that most influence the the amount of sales. Once we identify these characteristics, they can focus their monitoring efforts on product with a higher likelihood of improving sales.

The case of big mart sales can be treated as a regression problem. The goal is to forecast sales. The target variable in this case can be specified as a nominal variable, which are sales amount in a year

A wide range of machine learning algorithms can be used to solve the problem, we will use:

Linear regression techniques, such as LinearRegression, which use a linear function to predict the amount of sales.
Decision tree algorithms can be used to simulate more complex interactions between input factors and the target variable. RandomForestRegressor is a machine-learning model built from a collection of decision trees, each of which is trained on a different subset of training data. The program averages the predictions of all the trees to provide a final prediction.
To evaluate the performance of machine learning models, we will use various metrics, such as mean absolute error (MAE), mean squared error (MSE), root mean squared error (RMSE), R-Squared, mean absolute percentage error (MAPE).

