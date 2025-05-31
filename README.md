# Bulk-Metallic-Glass-BMG-Clustering-Project
This academic project explores the unsupervised clustering of Bulk Metallic Glasses (BMGs) based on their chemical compositions and thermal properties. It leverages preprocessing, feature engineering, dimensionality reduction, and clustering to discover meaningful patterns.


##  Dataset

The dataset includes:
- Alloy composition strings (e.g., `Zr 50 Cu 30 Al 20`)
- Thermal properties: `Tg(K)`, `Tx(K)`, `Tl(K)`

## Workflow Overview

###  Data Cleaning
- Loaded and cleaned the dataset
- Removed fully empty columns
- Parsed alloy composition strings using regular expressions to extract elemental percentages

### Data Preprocessing
- Missing values filled with zeros
- Applied `RobustScaler` to reduce the influence of outliers

###  Clustering

#### K-Means (after preprocessing)
- Applied after scaling and feature engineering
- Chose `k=2` based on Elbow Method and cluster evaluation metrics

####  DBSCAN
- Tested on the same preprocessed data
- Did not yield clearly separated clusters

###  Feature Engineering
Derived new features to better capture the alloy characteristics:
- `Nb_elements`: Number of elements in the alloy
- `Mean_pct`, `Std_pct`, `Max_elem_pct`: Descriptive stats of element percentages
- Thermodynamic ratios:
  - `Delta_T = Tx - Tg` (amorphous stability)
  - `Trg = Tg / Tl` (glass-forming ability)
  - `Reduced_Tx = Tx / Tl` (thermal stability)

#### Hierarchical Clustering
- Applied with Ward linkage
- Dendrogram supports the `k=2` decision with strong inter-cluster separation

### 5. Visualization
- Used **t-SNE** to project high-dimensional data into 2D
- Clear visual separation of clusters

### 6. Evaluation after featue engineering for example

| Metric                | Value     | Interpretation                                        |
|-----------------------|-----------|--------------------------------------------------------|
| Silhouette Score      | 0.810     | Strong cluster cohesion and separation                |
| Davies-Bouldin Index  | 0.267     | Very low overlap between clusters                     |
| Calinski-Harabasz     | 4048.57   | High inter-cluster variance                          |



##  Conclusion

This project demonstrates how domain-specific feature engineering combined with classical clustering techniques can reveal insightful patterns in material science data. The clustering results were validated visually (t-SNE, dendrogram) and quantitatively (Silhouette, DB, CH scores), showing a clear and robust separation of two alloy groups.
