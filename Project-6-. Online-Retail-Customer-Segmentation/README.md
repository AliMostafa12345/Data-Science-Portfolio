
# Customer Segmentation Using RFM Analysis and K-Means Clustering

## Project Overview

This project applies unsupervised machine learning to segment customers based on their purchasing behavior using the Online Retail dataset.

The project uses **RFM analysis (Recency, Frequency, and Monetary Value)** to transform retail transaction data into meaningful customer-level features. These features are then log-transformed, standardized, and analyzed using the K-Means clustering algorithm to identify distinct customer groups.

Four customer segments are created, and their characteristics are examined to understand differences in customer activity, purchasing frequency, and spending behavior.

The final clustering model achieves a **Silhouette Score of approximately 0.3355**, providing a quantitative measure of cluster separation and cohesion.

---

## Problem Statement

Understanding customer purchasing behavior helps businesses identify valuable customers, improve customer retention, and develop more effective marketing strategies.

However, transaction-level retail data does not directly reveal customer groups or purchasing patterns.

The objective of this project is to apply RFM analysis and unsupervised machine learning to group customers according to their purchasing recency, purchase frequency, and total spending.

The resulting segments can help businesses better understand their customer base and develop targeted strategies for different purchasing behaviors.

---

## Project Objectives

- Explore and clean retail transaction data.
- Remove records with missing customer identifiers and invalid transactions.
- Calculate customer-level Recency, Frequency, and Monetary Value.
- Apply logarithmic transformation to reduce feature skewness.
- Standardize RFM features before clustering.
- Investigate a suitable number of clusters using the Elbow Method.
- Apply K-Means clustering to identify four customer segments.
- Analyze the characteristics of each cluster.
- Visualize customer segments based on recency and monetary value.
- Evaluate clustering quality using the Silhouette Score.
- Export the customer segmentation results for further analysis.

---

## Dataset Description

The project uses the **Online Retail** dataset, which contains transactions from a UK-based online retail store.

The original dataset contains 541,909 transaction records and eight columns describing purchases, products, customers, and transaction dates.

### Dataset Features

| Feature | Description |
|---|---|
| `InvoiceNo` | Invoice identifier for a transaction |
| `StockCode` | Product or item identifier |
| `Description` | Product description |
| `Quantity` | Quantity of items purchased |
| `InvoiceDate` | Date and time of the transaction |
| `UnitPrice` | Price per unit |
| `CustomerID` | Customer identifier |
| `Country` | Country associated with the transaction |

### Data Cleaning

The dataset is cleaned using the following steps:

- Remove transactions without a `CustomerID`.
- Exclude cancelled orders identified by invoice numbers beginning with `C`.
- Remove transactions with zero or negative quantities.
- Remove transactions with zero or negative unit prices.
- Convert `InvoiceDate` into a datetime format.

After preprocessing, the dataset contains **397,884 valid transaction records**.

This filtering helps focus the analysis on identifiable customers and positive-value purchases.

---

## Technologies and Libraries

- **Python** — Programming language
- **Pandas** — Data cleaning, aggregation, and manipulation
- **NumPy** — Numerical operations and logarithmic transformation
- **Scikit-learn** — Feature scaling, K-Means clustering, and cluster evaluation
- **Matplotlib** — Data visualization
- **Seaborn** — Customer segment visualization

---

## RFM Analysis

RFM analysis is a customer analytics technique that evaluates customers based on three dimensions of purchasing behavior.

### 1. Recency

Recency measures the number of days since a customer's most recent purchase.

It is calculated as the difference between a reference date and the customer's latest invoice date.

In this project, the reference date is the latest invoice date available in the cleaned dataset.

**Interpretation:** Lower recency values indicate more recent purchasing activity.

### 2. Frequency

Frequency represents the number of distinct invoices associated with each customer.

It is calculated by counting the unique invoice numbers for every customer.

**Interpretation:** Higher frequency values indicate more frequent purchasing activity.

### 3. Monetary Value

Monetary value represents the total amount spent by each customer.

The transaction amount is calculated as:

`TotalPrice = Quantity × UnitPrice`

The transaction amounts are then summed for each customer.

**Interpretation:** Higher monetary values indicate greater total spending over the period represented by the dataset.

### RFM Feature Summary

| Feature | Calculation | Business Meaning |
|---|---|---|
| Recency | Days since the latest purchase | Customer activity |
| Frequency | Number of unique invoices | Purchase engagement |
| Monetary | Sum of transaction amounts | Total customer spending |

These three features provide a compact representation of customer purchasing behavior for clustering.

---

## Data Preprocessing and Feature Engineering

### 1. Customer-Level Aggregation

The cleaned transaction data is grouped by `CustomerID`.

Each customer is represented by three aggregated features:

- `Recency`
- `Frequency`
- `Monetary`

This transforms the original transaction-level dataset into a customer-level RFM dataset.

### 2. Logarithmic Transformation

The RFM features are transformed using `np.log1p()`.

This transformation reduces the influence of highly skewed values, particularly when a small number of customers have much higher spending or purchase frequency than most customers.

The transformation is applied before standardization.

### 3. Feature Scaling

StandardScaler is used to standardize the log-transformed RFM features.

Scaling is important because the original features have different numerical ranges and distributions.

Standardization helps prevent features with larger numerical magnitudes from disproportionately influencing the Euclidean distances used by K-Means.

---

## Clustering Methodology

### K-Means Clustering

K-Means is an unsupervised learning algorithm that partitions observations into a predefined number of clusters.

The algorithm assigns each customer to a cluster based on the distance between the customer's feature values and the cluster centroids.

The centroids are updated iteratively to reduce the within-cluster sum of squared distances.

In this project, K-Means is applied to the standardized RFM features to identify groups of customers with similar purchasing behavior.

### Selecting the Number of Clusters

The Elbow Method is used to investigate the appropriate number of clusters.

K-Means models are fitted for cluster counts ranging from 1 to 10, and their inertia values are recorded.

Inertia measures the within-cluster sum of squared distances between observations and their assigned cluster centroids.

The resulting values are plotted against the number of clusters to examine where the reduction in inertia begins to slow.

Based on the notebook's final configuration, **four clusters** are selected for customer segmentation.

### Final Clustering Configuration

| Parameter | Value |
|---|---|
| Algorithm | K-Means |
| Number of clusters | 4 |
| Random state | 42 |
| Number of initializations | 10 |
| Input features | Recency, Frequency, Monetary |
| Log transformation | `np.log1p()` |
| Feature scaling | StandardScaler |

---

## Customer Segmentation

After fitting the K-Means model, each customer receives a cluster label from 0 to 3.

The cluster labels are added to the RFM dataset, and the average RFM values for each cluster are calculated to support customer profiling.

The notebook's intended segment interpretations are described below.

### Cluster 3 — VIP Customers

This segment is interpreted as a high-value customer group characterized by frequent purchases and substantial total spending.

Potential business strategies include loyalty rewards, personalized offers, and premium customer experiences.

### Cluster 1 — Regular Customers

This segment is interpreted as customers with comparatively consistent purchasing activity and moderate spending.

Potential strategies include maintaining engagement, encouraging repeat purchases, and promoting relevant products.

### Cluster 0 — New or Occasional Customers

This segment is interpreted as customers with relatively recent activity but lower purchasing frequency or spending.

Potential strategies include introductory offers, targeted promotions, and campaigns designed to encourage additional purchases.

### Cluster 2 — Inactive Customers

This segment is interpreted as customers with less recent purchasing activity and comparatively low engagement.

Potential strategies include re-engagement campaigns, personalized discounts, and reminders about relevant products.

**Note:** These descriptions reflect the notebook's intended business interpretations. The actual segment characteristics should be confirmed using the calculated cluster averages. Cluster numbers are arbitrary labels and do not inherently indicate customer value or activity.

---

## Model Evaluation

### Silhouette Score

The Silhouette Score is used to evaluate the quality of the resulting clusters.

The score measures how similar each observation is to its assigned cluster compared with other clusters.

Silhouette Scores range from -1 to 1:

- **Close to 1:** Observations are generally well matched to their assigned clusters.
- **Around 0:** Clusters may overlap or observations may lie near cluster boundaries.
- **Below 0:** Some observations may be closer to other clusters than to their assigned cluster.

The project obtains the following result:

| Evaluation Metric | Result |
|---|---:|
| Number of clusters | 4 |
| Silhouette Score | 0.3355 |

The score indicates a moderate degree of cluster separation, with some potential overlap between customer segments.

It does not, by itself, prove that four clusters are optimal or that every segment has a clear business interpretation.

---

## Visualizations

### 1. Elbow Method

The Elbow Method plot shows how K-Means inertia changes as the number of clusters increases from 1 to 10.

It helps assess the trade-off between cluster compactness and model complexity when choosing the number of customer segments.

### 2. Customer Segments Scatter Plot

A scatter plot visualizes the customer segments using:

- **X-axis:** Recency
- **Y-axis:** Monetary Value
- **Color:** Assigned cluster

This visualization helps explore differences in customer activity and spending across the identified segments.

Although Frequency is included in the clustering process, it is not displayed in this two-dimensional plot. Customers that appear close together may therefore still differ in purchase frequency.

### 3. Cluster Summary

The average values of Recency, Frequency, and Monetary Value are calculated for each cluster.

This summary provides a numerical basis for comparing customer groups and assessing whether the intended segment labels accurately describe their purchasing behavior.

---

## Key Findings

- The original dataset contains 541,909 retail transaction records.
- Data cleaning reduces the dataset to 397,884 transactions.
- RFM analysis transforms transaction data into customer-level behavioral features.
- Logarithmic transformation and standardization prepare the features for distance-based clustering.
- K-Means is configured to divide customers into four segments.
- The Silhouette Score is approximately 0.3355, indicating moderate separation between clusters.
- Customer-level cluster summaries support comparisons of purchasing recency, frequency, and total spending.
- The resulting segments can serve as a starting point for customer profiling and targeted marketing analysis.

---

## Business Applications

### Targeted Marketing

Businesses can tailor campaigns to customer groups based on their purchasing patterns rather than using the same approach for every customer.

### Customer Retention

Customers with high recency values may benefit from re-engagement campaigns designed to encourage repeat purchases.

### Customer Loyalty

Customers with frequent purchases and high total spending may be suitable candidates for loyalty programs and personalized rewards.

### Revenue Analysis

Monetary values across segments can help businesses understand how spending is distributed across their customer base.

### Customer Relationship Management

RFM-based segmentation can support more structured customer profiling and help prioritize marketing activities.

These applications should be guided by the actual cluster statistics and validated against business outcomes.

---

## Limitations

- The analysis depends on three aggregated RFM features and does not incorporate product preferences, demographics, or other customer attributes.
- The reference date is derived from the latest invoice date in the dataset, so recency values depend on the period covered by the data.
- K-Means is sensitive to outliers and the choice of cluster count.
- The Elbow Method is a heuristic and does not independently establish the optimal number of clusters.
- A Silhouette Score of 0.3355 suggests that some overlap between clusters may remain.
- The scatter plot displays only two of the three features used for clustering.
- The proposed customer segment names require confirmation against the actual cluster averages.
- The analysis does not include independent validation or evidence that the segments improve marketing outcomes.

---

## Conclusion

This project demonstrates how RFM analysis and unsupervised machine learning can be combined to segment customers based on historical purchasing behavior.

The retail transaction data is cleaned and aggregated into Recency, Frequency, and Monetary Value features. These features are log-transformed and standardized before K-Means clustering is applied.

The final configuration identifies four customer segments, and the resulting clusters are evaluated using the Silhouette Score of approximately **0.3355**.

The project illustrates a practical approach to customer segmentation, providing a foundation for customer profiling, retention analysis, loyalty strategies, and targeted marketing. Further validation of cluster quality and segment characteristics would strengthen the reliability of the resulting business insights.

