### Project Title: Customer Segmentation for Targeted Marketing

#### Executive summary: This project analyzes customer purchasing behavior to improve marketing efficiency for an online retailer. By transforming transactional data into behavioral metrics (Recency, Frequency, Monetary value), we successfully identified distinct patterns in customer activity. Initial Exploratory Data Analysis (EDA) reveals a highly skewed customer base where a small percentage of "whales" drive the majority of revenue. A baseline K-Means clustering model was established to verify that mathematical segmentation is viable, achieving a positive Silhouette Score that suggests distinct groups exist within the data.

#### Rationale: 
In the competitive e-commerce landscape, "one-size-fits-all" marketing is inefficient and costly. Sending irrelevant offers to customers leads to low conversion rates and potential churn. By mathematically segmenting the customer base, the business can:

Optimize Budget: Focus resources on high-value customers.
Increase Engagement: Tailor messaging to specific behaviors (e.g., re-engaging dormant users vs. rewarding loyalists).
Improve ROI: Shift from mass marketing to precision targeting.

#### Research Question: 
How can we group customers based on their historical purchasing patterns to optimize marketing efforts and identify distinct customer personas?

#### Data Sources:
Source URL: UCI Machine Learning Repository - Online Retail II
Description: The dataset contains transaction-level data for a UK-based non-store online retail business between 01/12/2009 and 09/12/2011. Key features include InvoiceDate, Quantity, Price, and CustomerID.

#### Methodology:
Data Cleaning: Removed records with missing Customer IDs and handled negative quantities (returns) to ensure data quality.
Feature Engineering: Transformed raw transactions into an RFM (Recency, Frequency, Monetary) table, aggregating data at the customer level.
Preprocessing: Applied Log Transformation to handle heavy right-skew in the data and Standard Scaling to normalize features for distance-based algorithms.
Baseline Modeling: Implemented a K-Means Clustering algorithm (with K=3) to establish a baseline performance metric.

#### Results:
Data Distribution: The analysis confirmed that customer data follows a power law; the vast majority of customers are "one-time buyers," while a small segment purchases frequently.
Outliers: Significant outliers were detected in the Monetary value, necessitating robust scaling techniques.
Baseline Performance: The baseline K-Means model (K=3) produced a Silhouette Score of ~0.38 (score varies based on exact run), indicating that while clusters are forming, there is significant room for hyperparameter tuning to find the optimal separation between groups.

#### Next steps:
Hyperparameter Tuning: Utilize the "Elbow Method" and Silhouette Analysis to determine the mathematically optimal number of clusters.
Cluster Interpretation: Analyze the centroids of the final clusters to define business-friendly personas (e.g., "New High Spenders").
Advanced Modeling: Experiment with density-based clustering (DBSCAN) to better handle the outliers identified during EDA.

#### Outline of project:


##### Contact and Further Information:
For any questions, please contact me at sidharth.vaishnavi@gmail.com