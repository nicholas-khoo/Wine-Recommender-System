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

It was later discovered in the Terms of Use that the use of scrapping tools was prohibited, as such, the scraping step was abandoned. You may still find the python code written for the scraping process in the code folder - 00_Data_Collection.ipynb.

![Wine Enthusiast Magazine Terms of Use](https://github.com/nicholas-khoo/Wine-Recommender-System/blob/main/images/wine-mag-terms.png) </br>
Source: https://www.winemag.com/terms-of-use/

Instead of scraping the website, two sources of data were explored:
1) Wine Enthusiast Magazine dataset containing 130k reviews </br>
(https://www.kaggle.com/datasets/christopheiv/winemagdata130k)
2) Wine descriptors dataset from an existing github project </br>
(https://github.com/RoaldSchuring/wine_recommender)

# Data Dictionary
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
