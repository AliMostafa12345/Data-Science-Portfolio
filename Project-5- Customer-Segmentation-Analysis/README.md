
# Customer Segmentation Using K-Means Clustering

## Project Overview

This project applies unsupervised machine learning to segment customers based on their purchasing behavior using retail transaction data.

The objective is to identify groups of customers with similar spending patterns, purchase frequency, and purchasing quantities. K-Means clustering is used to divide customers into four distinct segments, helping uncover patterns that can support customer analysis and marketing strategy development.

The project covers data cleaning, customer-level feature engineering, feature scaling, cluster selection using the Elbow Method, clustering, cluster analysis, and visualization.

---

## Problem Statement

Understanding customer purchasing behavior is essential for businesses seeking to improve customer relationships, develop targeted marketing campaigns, and identify valuable customer groups.

The objective of this project is to group customers according to their historical purchasing behavior without using predefined labels.

By applying K-Means clustering to customer-level transaction features, the project aims to discover distinct customer segments based on spending, purchase frequency, and total items purchased.

---

## Project Objectives

- Explore and analyze retail transaction data.
- Handle missing customer identifiers.
- Transform transaction-level records into customer-level data.
- Engineer meaningful features representing customer purchasing behavior.
- Standardize numerical features before clustering.
- Use the Elbow Method to examine the appropriate number of clusters.
- Apply K-Means clustering to identify customer segments.
- Analyze the average characteristics of each cluster.
- Visualize customer segments using a scatter plot.
- Save the trained clustering model and feature scaler.

---

## Dataset Description

The project uses the **Online Retail** dataset, loaded from an Excel file named `Online Retail.xlsx`.

The original dataset contains **541,909 transaction records** and eight columns describing retail purchases.

### Dataset Features

| Feature | Description |
|---|---|
| `InvoiceNo` | Invoice identifier for a transaction |
| `StockCode` | Product or item identifier |
| `Description` | Product description |
| `Quantity` | Quantity of items in a transaction |
| `InvoiceDate` | Date and time of the transaction |
| `UnitPrice` | Price per unit |
| `CustomerID` | Customer identifier |
| `Country` | Customer's country |

### Data Quality Observations

- The original dataset contains 541,909 transaction records.
- The `CustomerID` column contains 135,080 missing values.
- The `Description` column contains 1,454 missing values.
- The dataset identifies 4,372 unique customers before records with missing customer IDs are removed.

Records without a customer identifier are excluded because they cannot be reliably assigned to individual customer segments.

---

## Technologies and Libraries

- **Python** — Programming language
- **Pandas** — Data manipulation and customer-level aggregation
- **Scikit-learn** — Feature scaling and K-Means clustering
- **Matplotlib** — Data visualization
- **Joblib** — Saving the trained model and scaler

---

## Data Preprocessing and Feature Engineering

### 1. Handling Missing Values

Rows with missing `CustomerID` values are removed to ensure that each transaction can be associated with a known customer.

Missing product descriptions are not explicitly removed because the clustering process does not use the `Description` column.

### 2. Calculating Total Spending

A new column, `TotalSpend`, is created by multiplying the quantity purchased by the unit price.

`TotalSpend = Quantity × UnitPrice`

This value represents the transaction amount calculated for each row before aggregation.

### 3. Customer-Level Aggregation

Transaction-level records are grouped by `CustomerID` to create one row per customer.

Three features are calculated:

| Feature | Description |
|---|---|
| `Total_Spend` | Sum of transaction amounts for each customer |
| `Number_of_Purchases` | Number of unique invoice identifiers associated with each customer |
| `Total_Items` | Sum of purchased quantities for each customer |

These features provide a simplified representation of customer purchasing behavior.

**Note:** The invoice count represents the number of unique invoices, not necessarily the number of separate shopping sessions.

### 4. Feature Selection

The following three features are selected for clustering:

- `Total_Spend`
- `Number_of_Purchases`
- `Total_Items`

These variables represent customer spending, purchase frequency, and purchasing volume.

### 5. Feature Scaling

StandardScaler is applied to standardize the selected features before clustering.

Scaling is important because the features have different numerical ranges. Without standardization, variables with larger numerical magnitudes could disproportionately influence the Euclidean distances used by K-Means.

---

## Clustering Methodology

### K-Means Clustering

K-Means is an unsupervised learning algorithm that partitions observations into a specified number of clusters.

The algorithm assigns each customer to a cluster based on the distance between the customer's feature values and the cluster centroids. It iteratively updates these centroids to reduce the within-cluster sum of squared distances.

In this project, K-Means is applied to the standardized customer-level features.

### Selecting the Number of Clusters

The Elbow Method is used to investigate a suitable number of clusters.

Separate K-Means models are fitted for cluster counts ranging from 1 to 10, and the corresponding inertia values are recorded.

Inertia measures the within-cluster sum of squared distances from observations to their assigned cluster centroids.

The inertia values are plotted against the number of clusters to help identify an elbow point, where additional clusters provide diminishing reductions in inertia.

Based on the project configuration, the final model uses **four clusters**.

### Final Clustering Configuration

| Parameter | Value |
|---|---|
| Algorithm | K-Means |
| Number of clusters | 4 |
| Random state | 42 |
| Number of initializations | 10 |
| Input features | 3 |
| Feature scaling | StandardScaler |

---

## Customer Segmentation

After fitting the K-Means model, each customer is assigned a cluster label from 0 to 3.

The cluster labels are added to the customer-level dataset, allowing the characteristics of the four groups to be examined.

The project calculates the average values of the selected features for each cluster.

### Cluster Analysis

The four clusters represent groups of customers with different combinations of spending, purchase frequency, and total purchasing quantities.

The notebook's intended interpretations are:

- **Cluster 0 — Low-Value Customers:** Customers associated with relatively low purchasing value.
- **Cluster 1 — Loyal High-Value Customers:** Customers characterized by relatively high spending and recurring purchases.
- **Cluster 2 — Regular Customers:** Customers with comparatively typical purchasing patterns.
- **Cluster 3 — Premium/VIP Customers:** Customers representing a potentially high-value segment.

These descriptions are preliminary interpretations rather than verified cluster profiles. The actual characteristics of each group should be confirmed using the calculated cluster averages before assigning definitive business labels.

Cluster numbers are arbitrary identifiers and do not inherently indicate customer value or ranking.

---

## Visualizations

### 1. Elbow Method

The Elbow Method plot displays the relationship between the number of clusters and K-Means inertia.

It helps assess how increasing the number of clusters affects the compactness of the resulting groups.

### 2. Customer Segmentation Scatter Plot

A scatter plot visualizes customers using:

- **X-axis:** `Total_Spend`
- **Y-axis:** `Number_of_Purchases`
- **Color:** Assigned cluster label

The visualization provides a two-dimensional view of the customer segments based on spending and purchase frequency.

Although the clustering model uses all three standardized features, the scatter plot displays only two features. Therefore, customers that appear close together in this plot may still differ in their total purchasing quantities.

### 3. Cluster Summary

The mean values of `Total_Spend`, `Number_of_Purchases`, and `Total_Items` are calculated for each cluster.

This summary supports comparisons between customer segments and helps identify which groups exhibit higher or lower values for the selected purchasing features.

---

## Key Findings

- The original retail dataset contains 541,909 transaction records.
- Customer-level aggregation transforms transaction records into behavioral features for individual customers.
- Three numerical features are used to represent spending, purchase frequency, and purchasing volume.
- StandardScaler is applied before clustering to prevent differences in feature scales from dominating distance calculations.
- The Elbow Method is used to investigate cluster counts between 1 and 10.
- K-Means is configured to identify four customer segments.
- Cluster summaries and scatter plots support the interpretation of the resulting customer groups.
- The resulting segments can provide a starting point for customer profiling and targeted marketing analysis.

---

## Business Applications

Customer segmentation can support several business activities:

- **Targeted Marketing:** Develop campaigns tailored to different purchasing patterns.
- **Customer Retention:** Identify customer groups that may benefit from loyalty initiatives.
- **Customer Value Analysis:** Compare segments by spending and purchasing volume.
- **Personalized Offers:** Design promotions based on observed purchasing behavior.
- **Business Strategy:** Better understand differences between customer groups when planning marketing activities.

The usefulness of these applications depends on the actual cluster profiles and further business validation.

---

## Model Persistence

The project saves two fitted objects using Joblib:

- `customer_segmentation_model.pkl` — The trained K-Means model.
- `customer_segmentation_scaler.pkl` — The fitted StandardScaler.

Saving both objects preserves the clustering configuration and the feature-scaling parameters used during training.

---

## Limitations

- The analysis depends on three aggregated purchasing features and does not incorporate every available transaction attribute.
- Missing customer identifiers are excluded, which may affect the representativeness of the analyzed customer population.
- Negative quantities or unusual transaction values, if present, may influence spending and quantity aggregates.
- K-Means is sensitive to outliers and the choice of cluster count.
- The Elbow Method is a heuristic and does not independently establish that four clusters are optimal.
- The scatter plot shows only two of the three clustering features.
- Customer segment descriptions should be validated against the calculated cluster averages.
- No quantitative clustering evaluation metrics, such as silhouette score, are reported in the notebook.

---

## Conclusion

This project demonstrates how unsupervised machine learning can be used to segment retail customers according to their historical purchasing behavior.

Transaction-level data is transformed into customer-level features representing total spending, number of purchases, and total items purchased. After standardization, K-Means clustering is used to create four customer segments.

The Elbow Method, cluster summaries, and scatter plot provide tools for exploring the structure of these segments and comparing customer purchasing patterns.

Overall, the project illustrates a practical customer segmentation workflow that can support exploratory customer analytics and marketing strategy development. Further validation of cluster quality and segment characteristics would strengthen the business interpretations.

