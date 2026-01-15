### Required Capstone Project 24.1: Final Report
**Customer Segmentation for Targeted Marketing: A Data-Driven Approach**

#### Summary
I tackled the challenge of marketing efficiency for a UK-based online retailer by analyzing their transactional data. My approach used unsupervised machine learning—specifically K-Means Clustering and DBSCAN—to segment the customer base into distinct personas based on how they buy. The analysis paid off: I successfully identified key segments like "Champions" and "At-Risk" customers. This gives the business a clear roadmap to personalize campaigns, boost retention, and allocate their budget where it counts.

#### Define the Problem Statement
In the competitive world of e-commerce, the "one-size-fits-all" approach just doesn't cut it anymore. We can't keep sending the same discount email to a loyal big-spender and a one-time buyer—it wastes margin on one and relevance on the other. It's time to stop doing this!
* **The Business Problem:** This UK retailer had a blind spot: they couldn't see who their best customers were or which high-value ones were about to churn.
* **The Goal:** I wanted to group customers mathematically. This allows marketing to be tailored to specific needs, ultimately driving up ROI and Customer Lifetime Value (CLV).

#### Research Question
**Can we identify distinct customer segments based on historical buying patterns to tailor marketing strategies and reduce churn?**

**Potential Benefits:** Solving this problem allows the business to move from mass marketing to precision targeting. This leads to:
* **Optimized Budget:** We can stop wasting money and start allocating high-cost retention efforts (like discounts) only to those "At-Risk" high-value customers.
* **Increased Engagement:** Messaging can now be tailored to specific behaviors, like offering "Early Access" to our loyalists.
* **Improved ROI:** We can maximize the return on marketing spend by targeting the right user with the right message.

### Model Outcomes or Predictions
* **Type of Learning:** Unsupervised Learning.
* **Algorithm Type:** Clustering.
* **Expected Output:** My model outputs a discrete **Cluster Label** (0, 1, 2, 3...) for each unique customer. These labels map directly to business personas (e.g., "Champions," "Loyalists," "Hibernating") to guide downstream marketing actions. Since this is unsupervised learning, there's no "ground truth" label to predict; the outcome is discovering the inherent structures within the data itself.

### Data Acquisition
**Data Source:** I used the **Online Retail II Data Set** from the UCI Machine Learning Repository.
* **Source:** [UCI Machine Learning Repository - Online Retail II](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)
* **Description:** This dataset holds transaction-level data for a UK-based non-store online retail business between 01/12/2009 and 09/12/2011.

**Analysis of Data Utility:**
The raw data included `InvoiceDate`, `Quantity`, `Price`, and `CustomerID`. While raw transactions aren't directly usable for segmentation, they contained exactly what I needed to engineer **RFM (Recency, Frequency, Monetary)** features—the industry standard for determining customer value.

### Data Preprocessing/Preparation
To get the data ready for machine learning, I took these steps:

**1. Data Cleaning:**
* **Missing Values:** I dropped rows with missing `Customer ID` (about 20% of the data), since anonymous transactions can't be segmented into customer profiles.
* **Inconsistencies:** I removed transactions with negative `Quantity` (returns or cancellations) to prevent skewing the total spend metrics.

**2. Feature Engineering:**
* I aggregated raw transactional rows by `Customer ID` to create a new dataset with three key features:
    * **Recency:** Days since the last purchase.
    * **Frequency:** Total count of unique invoices.
    * **Monetary:** Sum of (`Quantity` * `Price`).

**3. Transformations and Scaling:**
* **Log Transformation:** The RFM data was highly right-skewed. I applied a Log transformation to normalize the distributions, making them more suitable for K-Means.
* **Scaling:** I used a `StandardScaler` to normalize features to a mean of 0 and standard deviation of 1. This ensures that the "Monetary" feature (with its large dollar values) doesn't dominate the "Frequency" feature (with its small count values) during distance calculations.

**4. Data Splitting:**
* Since this is an **Unsupervised Learning** task aimed at pattern discovery rather than predicting future labels, I fitted the model on the entire processed dataset. This maximized the density and accuracy of the clusters formed.

### Modeling
I selected and compared two distinct machine learning algorithms:

1.  **K-Means Clustering:**
    * I chose this as the primary model for its efficiency and ability to force every customer into a specific segment, which is ideal for marketing coverage (no customer is left unassigned).
2.  **DBSCAN (Density-Based Spatial Clustering of Applications with Noise):**
    * I selected this as a comparative model for its ability to identify outliers. This was useful for detecting "Noise" points that might represent fraudulent transactions or extreme "Whales" that skew averages.

### Model Evaluation
**Models Considered:** Unsupervised Clustering (K-Means vs. DBSCAN).

**Evaluation Metrics:**
Since ground truth labels do not exist, I used intrinsic metrics:
* **Elbow Method (Inertia):** To find the point of diminishing returns where adding more clusters doesn't significantly improve compactness.
* **Silhouette Score:** To measure how similar an object is to its own cluster (cohesion) compared to other clusters (separation).

**Determination of Optimal Model:**
* **DBSCAN Results:** While effective at outlier detection, DBSCAN categorized too many varied customers as "Noise," making it difficult to operationalize for a mass-marketing strategy.
* **K-Means Results:** The K-Means model proved to be the most optimal. Using the Elbow Method, I identified **K=4** as the best balance between mathematical performance and business interpretability.
    * The model achieved a **Silhouette Score of ~0.38**, indicating distinct separation.
    * The 4 clusters mapped cleanly to actionable business tiers: **"Champions"** (High Value), **"Loyalists"** (Steady), **"At-Risk"** (Waning Interest), and **"Hibernating"** (Low Value). This direct mapping to business strategy made K-Means the superior choice for this problem statement.