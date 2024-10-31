### Problem Statement

This project examines how proximity to mass transit impacts residential property prices in Bangkok, focusing on the main question: is there a correlation between distance from a station and property prices? We begin by comparing prices of properties located within 1 kilometer of a station with those located farther away.

Next, we explore how distance from the station affects property prices and identify the five stations with the most significant impact on nearby property values. Our approach uses recent residential data in Bangkok around BTS Skytrain and MRT subway stations, applying machine learning models to rank stations based on the relationship between distance and nearby property prices. This ranking helps reveal if prices tend to increase or decrease as the distance from each station changes.


---

### Data Dictionary

[`The dataset`](../Dataset/train.json) provides details on Bangkok housing prices and various property characteristics. Key columns are described below:

| Column                | Data Type    | Description                                                                                             |
|-----------------------|--------------|-----------------------------------------------------------------------------------------------------|
| `id`                    | int       | ID of selling item                                                                                      |
| `province`              | string    | Province name: this dataset only includes Bangkok, Samut Prakan, and Nonthaburi                         |
| `district`              | string    | District name                                                                                           |
| `subdistrict`           | string    | Subdistrict name                                                                                        |
| `address`               | string    | Address, e.g., street name, area name, soi number                                                       |
| `property_type`         | string    | Type of the house: Condo, Townhouse, or Detached House                                                  |
| `total_units`           | float     | The number of rooms/houses that the condo/village has                                                   |
| `bedrooms`              | int       | The number of bedrooms                                                                                  |
| `baths`                 | int       | The number of baths                                                                                     |
| `floor_area`            | float     | Total area of inside floor [㎡]                                                                          |
| `floor_level`           | int       | Floor level of the room                                                                                 |
| `land_area`             | float     | Total area of the land [㎡]                                                                             |
| `latitude`              | float     | Latitude of the house                                                                                   |
| `longitude`             | float     | Longitude of the house                                                                                  |
| `nearby_stations`       | int       | The number of nearby stations (within 1km)                                                              |
| `nearby_station_distance` | list   | List of (station name, distance[m]). Each station name consists of station ID, station name, and Line, such as "E4 Asok BTS" |
| `nearby_bus_stops`      | int       | The number of nearby bus stops                                                                          |
| `nearby_supermarkets`   | int       | The number of nearby supermarkets                                                                       |
| `nearby_shops`          | int       | The number of nearby shops                                                                              |
| `year_built`           | int       | Year built                                                                                              |
| `month_built`           | string    | Month built: January-December                                                                           |
| `price` ( **Target Value** )                 | float     | Selling price                                                                            |



---

### Methodology

This study employs the following methodology to predict housing price :

**1. Data Cleaning and EDA** 

Handle missing values then analyze patterns and relationships using visualizations in [`EDA.ipynb`](./Code/Cleaning_Data.ipynb).

**2. Preprocessing** 

Transform data by encoding categorical features and polynomial features to prepare for modeling in [`Preprocess.ipynb`](./Code/Preprocess.ipynb).

**3. Modeling & Benchmarks** 

Train and tune multiple models, evaluating each against a baseline to select the best model for the task in [`Model_Benchmarks.ipynb`](./Code/Model_Benchmarks.ipynb).

**4. Evaluation and Conceptual Understanding** 

Assess model accuracy and interpret results to ensure the model aligns with project goals, summarized in [`Evaluation.ipynb`](./Code/Best_Model.ipynb).

---

### Findings 



This analysis yields insights into how station proximity relates to housing prices:
- Housing prices increase by approximately **446,240 THB** for each additional MRT or BTS station within 1 km.
- The five stations with the strongest influence on housing prices, based on data samples (n > 50), are as follows:

| Station                | price (bath) / 100 meters closer  
|-----------------------|-----------|
| `MRT Phetchaburi	`                  |      353,425       |
| `MRT Sam Yan`              | 312,668    |
| `BTS Nana`              | 282,391    |
| `BTS Phra Khanong`           | 267,761    |
| `MRT Phetkasem 48`               | 263,752    |

---

### Visualizations
To support the findings, the following figures are included:

* [`corr_all_numeric_features`](../Figures/corr_all_numeric_features.png) : Shows correlations among all numerical variables in the dataset.
* [`corr_with_price`](../Figures/corr_with_price.png) : Shows features with a correlation to price and missing values under 20%.
* [`pair_strongcorr_features`](../Figures/pair_strongcorr_features.png) : Displays the relationship among `baths`, `bedrooms`, `floor_area` .
* [`top_5_stations`](../Figures/top_5_stations.png) : Identifies the five stations with the most significant effect on housing prices.


---

### Conclusion
 The study suggests that proximity to mass transit stations strongly influences housing prices in Bangkok. These findings can support buyers and developers in assessing location-based property value trends.





---

### Futher Work

Further research will explore additional variables that might influence housing prices in relation to station distance.
