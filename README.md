# Background

The wine industry is a booming, multi-billion dollar sector that continues to grow rapidly. However, with the overwhelming selection of wines available, choosing the perfect one can be a daunting task for many consumers. Wine tasting is a subjective experience that requires a certain level of expertise that may not always be accessible to the average consumer. As a result, there is a growing demand for a reliable and efficient wine recommendation system that can help individuals select wines based on their personal preferences.

To address this challenge, wine recommendation systems have been developed. These systems utilize machine learning algorithms to analyze various data points, such as wine type, flavor, aroma, region, vintage, and price, to provide personalized recommendations to customers. Studies have shown that these systems are highly effective in providing accurate wine recommendations, resulting in increased customer satisfaction and loyalty.

# Project Goals

The aim of this project is to create a wine recommendation system that is precise and efficient, providing benefits to both customers and wine industry stakeholders.

There is a requirement for a wine recommendation system that can generate personalized recommendations based on individual taste preferences, occasions, and food pairing. However, there is currently a lack of a dependable and efficient wine recommendation system that can provide accurate recommendations by considering a comprehensive range of data points.

Therefore, the developed system must address these challenges and offer an effective marketing tool for wine products while improving customer satisfaction and loyalty.

# Benefits

This analysis will provide customers with personalized recommendations based on their individual taste preferences, occasion, and food pairing. The system's reliability and efficiency will enable it to conquer the challenges of selecting the right wine for specific occasions, meals, or personal taste preferences, offering dependable and efficient wine recommendations.

The system's potential to increase customer satisfaction and loyalty provides wineries and wine brands with an effective marketing tool. By providing an accurate and efficient wine recommendation system, this project intends to bring commercial value to both consumers and wine industry stakeholders.

# Data Collection

Data was originally scrapped from Wine Enthusiast Magazine (https://www.winemag.com/wine-ratings/), often abbreviated as WineMag or Winemag, a lifestyle magazine covering wine, food, travel, and entertaining topics. It was founded in 1988 and is based in New York City. The magazine is known for its ratings and reviews of wines from around the world, as well as its coverage of wine regions, wine-making techniques, and food pairings. WineMag is also recognized for its annual wine awards, including the Wine Star Awards, which honor excellence in the wine industry.

It was later discovered that the use of scraping tools within the site was prohibited, as such, this step was halted to prevent infrindgements with the terms of use. You may still find the python code written for the scraping process in the code folder and in the notebook "00_Data_Collection.ipynb".

![Wine Enthusiast Magazine Terms of Use](https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/wine-mag-terms.png) </br>
Source: https://www.winemag.com/terms-of-use/

In continuation with the project, two other sources of data were explored:
1) Wine Enthusiast Magazine dataset containing 130k reviews </br>
(https://www.kaggle.com/datasets/christopheiv/winemagdata130k)

2) Wine descriptors dataset from an existing github project </br>
(https://github.com/RoaldSchuring/wine_recommender)

# Data Dictionary

The datasets were cleaned to produce the resulting features. These features were later used in exploratory data analysis to uncover more insights surrounding wine as well as in machine learning, to build the recommender system.

## Wine Reviews

|Feature|Type|Description|
|---|---|---|
|country|object|The country where the wine was produced.|
|description|object|Description of the wine's characteristics and tasting notes|
|designation|object|The vineyard within the winery where the grapes for the wine were sourced from.|
|points|int64|The number of points assigned to the wine on a scale of 1-100 by the wine reviewer.|
|price|float64|The price of a bottle of the wine.|
|province|object|The province or state within the country where the wine was produced.|
|region_1|object|The first-level region within the province or state where the wine was produced (e.g. Napa Valley).|
|region_2|object|The second-level region within the province or state where the wine was produced (e.g. Rutherford within Napa Valley).|
|taster_name|object|The name of the wine reviewer.|
|taster_Twitter_handle|object|The Twitter handle of the wine reviewer.|
|title|object|The title of the wine review.|
|variety|object|The type of grape used to produce the wine.|
|winery|object|The name of the winery that produced the wine.|

## Wine Descriptors

|Feature|Type|Description|
|---|---|---|
|raw descriptor|object|A descriptor for a sensory attribute of the food or drink being evaluated (e.g. "sweetness", "acidity", "herbaceousness", etc.).|
|level_3|object|A subcategory of the descriptor that provides additional detail about the attribute being evaluated (e.g. "fruit sweetness" for the "sweetness" descriptor).|
|level_2|object|A broader category that groups together related descriptors and level_3 subcategories (e.g. "flavor").|
|level_1|object|The highest level of categorization that groups together the level_2 categories (e.g. "aroma and flavor").|

# Exploratory Data Analysis

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Wine%20Prices%20Distribution.png" alt="Wine Prices Distribution" />
</p>
Distribution of wine prices is heavily right-skewed with majority of the wines being priced below approximately USD 100.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Wine%20Rating%20Distribution.png" alt="Wine Ratings Distribution" />
</p>
Wines with ratings of 90-92 are the most common in the dataset. This suggests that these ratings may be the most "typical" or "average" for wines in this dataset.

</br> Wines with ratings below 89 or above 95 are relatively rare, with fewer than 500 wines receiving these ratings. This suggests that wines with extreme ratings are less common in the dataset, which could be due to a variety of factors, such as the scoring criteria used by the tasters, the selection of wines in the dataset, or other factors.

There are only a small number of wines in the dataset with ratings above 95. This could suggest that these wines are particularly rare or exceptional, and may be of particular interest to wine enthusiasts or collectors.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Rating%20%26%20Price%20Correlation.png" alt="Ratings vs Prices Correlation" />
</p>
There is a slight correlation between "points" and "price", but not a very strong one.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Mean%20Points%20by%20Province.png" alt="Mean Points by Province" />
</p>
Wines produced in California tend to receive higher ratings on average than wines produced in the other three states. This could be due to a variety of factors, such as the climate and geography of the region, the types of grapes that are grown there, the expertise of the winemakers, or the reputation of the region.

</br> Similarly, the fact that Oregon and Washington have higher average ratings than New York suggests that there may be differences in the quality of wines produced in these regions, or differences in the preferences of wine critics and consumers.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Average%20Price%20by%20Province.png" alt="Average Price by Province" />
</p>
These regions may produce higher quality wines as consumers are often willing to pay a premium for them, and production costs may be higher as well, which consequently drives up the price of the wines.

</br> Additionally, the higher demand for wines from these regions compared to wines from other regions could also contribute to the higher prices observed.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Top%2010%20Words.png" alt="Top 20 Words" />
</p>

`flavors`, `fruit`, and `cherry`: These words suggest that wine drinkers pay close attention to the taste of the wine and the presence of fruit flavors, particularly cherry. This could be useful information for winemakers who are interested in creating wines with strong and enjoyable flavors.

`aromas` and `nose`: These words suggest that wine drinkers pay attention to the wine's aroma or scent. This could be useful information for winemakers who want to create wines with a pleasant and distinctive aroma.

`acidity` and `tannins`: These words suggest that wine drinkers pay attention to the structure and balance of the wine. Both acidity and tannins are important components of a wine's structure, and their presence and balance can have a significant impact on the wine's overall flavor and quality.

`palate` and `finish`: These words suggest that wine drinkers pay attention to the overall experience of drinking the wine, including the way it feels in the mouth and the aftertaste. This information could be useful for winemakers who are interested in creating wines that offer a satisfying and enjoyable drinking experience from start to finish.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Top%2010%20Bigrams.png" alt="Top 10 Bigrams" />
</p>
Fruit flavors are highly emphasized in the descriptions, with `fruit flavors` and `cherry fruit` being two of the bigrams. Other common descriptors include `full-bodied`, `black cherry`, `black pepper`, and `dark chocolate`.

</br> The mention of specific grape varieties such as `cabernet sauvignon`, `cabernet franc`, and `petit verdot` also indicates that these grapes are popular and commonly used in winemaking.

The use of terms like `french oak` suggests that the type of oak used for aging may also be an important factor in the flavor profile of the wines.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/Wordcloud.png" alt="Word Cloud" />
</p>
Similarly to the Top 10 words, the word cloud provides a better visual representation of the most frequent words appearing in the wine reviews.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/sentimentscore.png" alt="Sentiment Score" />
</p>
Majority of the sentiments have a positive sentiment. The negative sentiment scores are more spread out and less frequent, which results in a left-skewed distribution.

</br> The mean score being 0.56 indiciates that the overall sentiment of the wine reviews is positive.

# Machine Learning

The following models were trained and FunkSVD performed the best among the 11 models. </br>
|Model|ave_precision@k_score|ave_recall@k_score|
|---|---|---|
|**FunkSVD**|**0.867917**|**0.257780**|
|SVD|0.865417|0.257334|
|Baseline Predictor|0.822917|0.251537|
|KNN Baseline|0.822917|0.251537|
|Slope One|0.805417|0.250240|
|KNN Basic|0.805417|0.250240|
|KNN Means|0.805417|0.250240|
|KNN ZScore|0.805417|0.250240|
|Co-clustering|0.802917|0.249946|
|Normal Predictor|0.719583|0.205594|
|NonNegative Matrix Factorization|0.715417|0.246805|

Hyperparameter tuning was then performed on FunkSVD to further enhance the performance. The final results are below:

|Model|ave_precision@k_score|ave_recall@k_score|
|---|---|---|
|**Tuned FunkSVD**|**0.952778**|**0.225906**|
|FunkSVD|0.867917|0.257780|
|SVD|0.865417|0.257334|
|Baseline Predictor|0.822917|0.251537|
|KNN Baseline|0.822917|0.251537|
|Slope One|0.805417|0.250240|
|KNN Basic|0.805417|0.250240|
|KNN Means|0.805417|0.250240|
|KNN ZScore|0.805417|0.250240|
|Co-clustering|0.802917|0.249946|
|Normal Predictor|0.719583|0.205594|
|NonNegative Matrix Factorization|0.715417|0.246805|

The tuned FunkSVD model was then tested to produce the top 10 recommendations of wine and compared to their actual rating to assess the model's capability to provide similar recommendations. The evaluation is done by creating a dataframe with the estimated match score (predicted ratings) for wines not previously rated by the user.

The predictions are then made by the chosen model and are based on the user's past wine ratings.

<p align="center">
  <img src="https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/recommended%20wines.png" alt="Wine Recommender" />
</p>

Based on the results, it appears that the recommender is performing well as the top 10 recommendations have high estimated match points (above 91) and high actual ratings (ranging from 94 to 100). 

# Conclusion

The tuned FunkSVD model performed the best, producing an average precision@k score of 0.952778 and an average recall@k score of 0.225906.

These results suggests that the developed recommender system is effective in generating personalized recommendations based on individual taste preferences, occasions, and food pairing.

# Limitations and Further Exploration

The goal of the project is to build a simple wine recommender system. The dataset used in the project may not be representative of the entire wine industry and may not include all relevant features that could impact wine recommendations.

Future exploration could include exploration of a larger dataset with more wine features to provide a more comprehensive wine recommender system.
