### Required Assignment 11.1: What Drives the Price of a Car?

**Context:** The client is a used car dealership. They want to know what features (mileage, year, brand, etc.) consumers value the most so they can stock their inventory with cars that will sell for higher prices.

**Objective:**  goal is to understand what factors make a car more or less expensive. As a result of your analysis, you should provide clear recommendations to your client—a used car dealership—as to what consumers value in a used car. In other words, the goal will be to build a predictive model that estimates the price of a used car based on its attributes. By analyzing the model's coefficients (feature importance), we will identify the key drivers of price (e.g., does a diesel engine add more value than low mileage?).

**Data:** We have a dataset from Kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure the speed of processing. The objectives require using **Regression** to solve the problem. We aim to minimize the prediction error (MSE or MAE) and maximize the $R^2$ score to ensure our model explains the variance in car prices effectively.

**Data Understanding:** We load the data and check for quality issues such as missing values, duplicates, or outliers (e.g., a car price of $0).

**Deliverables:** After understanding, preparing, and modeling your data, provide a basic report that details your primary findings. Your audience for this report is a group of used car dealers interested in fine-tuning their inventory.

@Findings 

**Summary:**
We analyzed over 400,000 used car listings to determine the key factors that drive price. Our model explains approximately 65% of the price variation.

**Key Findings:**

1.  **Car Age & Mileage:** As expected, these are the strongest negative drivers. Every year of age and every 10k miles significantly drops the value.
2.  **Engine Type:** Vehicles with **Diesel** engines tend to command a higher premium compared to gas engines.
3.  **Vehicle Type:** **Trucks** and **Pickups** hold their value better than Sedans.
4.  **Drive:** **4WD** (Four-Wheel Drive) features are positively correlated with higher prices.
5.  **Brand:** Brands like Ferarri, Aston Martin, Tesla appear as high-value outliers, while common brands have lower coefficients.

**Recommendations:**

* **Acquisition:** Focus on acquiring newer diesel trucks or 4WD vehicles, as these features command the highest premiums.
* **Inventory:** Be cautious with high-mileage sedans; they depreciate the fastest.
* **Marketing:** Highlight "Diesel" and "4WD" prominently in listings, as consumers value these specific features highly.