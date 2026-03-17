# Gene-Expression-Clustering-using-PCA-KMeans-and-t-SNE

**📌 Problem Statement**

The gene expression dataset used in this study has high dimensionality, consisting of a large number of features (genes), which introduces:

Noise

Redundancy

Computational complexity

Difficulty in identifying meaningful structure

-------------

**The objective of this project is to:**

Reduce the dimensionality of the dataset while preserving important information

Apply clustering to identify natural groupings in the data

Evaluate the quality of the resulting clusters using quantitative metrics

------

**📂 Dataset**

This project uses a gene expression dataset from the UCI Machine Learning Repository.

The dataset contains:

High-dimensional numerical gene expression values(16,382)

Multiple samples with potentially complex relationships

------

**⚙️ Methodology**

The analysis steps are:

Data inspection

Data standardization

PCA (full fitting for variance analysis)

Scree plot & cumulative variance

PCA dimensionality reduction

K-Means clustering

Cluster evaluation

t-SNE visualization

-----------

**🔍 1️⃣ Data Inspection**

✔️ Steps Performed

Checked dataset shape

Checked missing values

Generated descriptive statistics


**⚖️ 2️⃣ Data Standardization**

✔️ What was done

Applied StandardScaler to all features

❓ Why this is necessary

Both PCA and K-Means rely on distance calculations.

Without scaling:

Features with larger magnitudes dominate

Variance becomes biased

Standardization ensures:

Equal contribution of all features

Mean = 0, Variance = 1

Reliable dimensionality reduction and clustering

------

**📉 3️⃣ Initial PCA (Full Component Extraction)**

pca_full = PCA(n_components=None)
pca_full.fit(X_scaled)

It was required to compute:

Explained variance ratio for all components

Because:

The number of components cannot be chosen arbitrarily

It must be based on how variance is distributed

which enables:

Scree plot generation

Cumulative variance analysis

-----

**📊 4️⃣ Scree Plot & Cumulative Variance**

✔️ What was done

Plotted explained variance per component

Computed cumulative explained variance

❓ Why this is necessary

Identifies how much information each component retains with 90% variance

Supports informed selection of components

<img width="1592" height="756" alt="Screenshot (539)" src="https://github.com/user-attachments/assets/2db65d03-08d1-4868-b972-c445512f04b1" />

<img width="1592" height="730" alt="Screenshot (540)" src="https://github.com/user-attachments/assets/b51ca96f-76b8-4a61-b100-5ad4b5bfadfc" />

------

**🎯 5️⃣ PCA Component Selection**

✔️ Initial Choice

350 components (~90% variance retained)

❓ Justification

90% variance is a common threshold

Balances:

Information retention

Dimensionality reduction

⚠️ Limitation

High variance retention may include noise

Too many components can negatively affect clustering

--------

**🔄 6️⃣ PCA Transformation**

Transformed scaled data into reduced feature space

❓ Why this is necessary

Produces uncorrelated components

Reduces dimensionality

Prepares data for clustering

---------

**🤖 7️⃣ K-Means Clustering**

❓ Why K-Means

Efficient for large datasets

Works well with numerical features

----------

**📐 8️⃣ Choosing Number of Clusters (K)**

✔️ Method Used

Elbow Method (Inertia vs K)

❓ Justification

Prevents arbitrary selection of K

------

**📏 9️⃣ Cluster Evaluation (350 PCA Components)**

✔️ What was done

The clustering results obtained using 350 PCA components were evaluated using:

Silhouette Score

Davies-Bouldin Index

📊 Results

Silhouette Score: 0.1616

Davies-Bouldin Index: 2.4302

❓ Why this step is necessary

Clustering is an unsupervised task, meaning:

There are no ground truth labels

Performance cannot be assessed using traditional accuracy metrics

Therefore, internal evaluation metrics are required to:

Measure how well data points fit within their clusters

Assess how distinct the clusters are from each other

-----

**🔍 Interpretation**

The low silhouette score indicates that data points are not well separated and clusters overlap

The high Davies-Bouldin Index suggests poor separation between clusters

-------

**⚠️ Conclusion**

The clustering performance using 350 components is suboptimal, indicating that:

High variance retention does not guarantee meaningful clustering

The dimensionality may still be too high for effective separation

---------

**🔄 🔟 Model Refinement**

✔️ Adjustment

Reduced PCA components to 100

❓ Why this was necessary

High dimensionality weakens distance-based clustering

Reducing components:

Removes noise

Improves separability


**📈 1️⃣1️⃣ Cluster Evaluation (100 PCA Components)**

✔️ What was done

After reducing the dimensionality to 100 PCA components, the clustering results were evaluated using:

Silhouette Score

Davies-Bouldin Index

📊 Results

Silhouette Score: 0.2115

Davies-Bouldin Index: 1.9459

❓ Why this step is necessary

Following the adjustment in dimensionality, it is necessary to re-evaluate clustering performance to determine whether:

Cluster cohesion has improved

Cluster separation has increased

This ensures that the modification (reducing components) leads to a measurable improvement rather than an arbitrary change.

-----------

**🔍 Interpretation**

The increase in silhouette score indicates better-defined clusters with reduced overlap

The decrease in Davies-Bouldin Index suggests improved separation between clusters

✅ Conclusion

Reducing the number of PCA components from 350 to 100 resulted in:

Improved cluster quality

Better separation and structure in the data

This confirms that:

Lower dimensional representations can enhance clustering performance

Not all retained variance contributes positively to cluster formation

-------------

**🎨 1️⃣2️⃣ Visualization using t-SNE**

❓ Why t-SNE

Captures non-linear relationships

Preserves local structure

Provides intuitive 2D visualization

---------

**🚀 Conclusion**

This project demonstrates a complete unsupervised learning pipeline for high-dimensional biological data.

The final approach achieves a balance between:

Information retention

Noise reduction

Cluster quality
