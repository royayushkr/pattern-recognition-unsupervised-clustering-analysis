# Penguin Species Clustering

## Project Overview
Researchers collecting data on penguins in Antarctica have been unable to record the specific species of every bird observed. They are aware that at least three species (Adelie, Chinstrap, and Gentoo) exist in the region. This project utilizes unsupervised learning techniques to identify distinct groups within the dataset, helping researchers classify penguins based on their physical features.

## Dataset
The project utilizes `penguins.csv`, which contains physical measurements of penguins collected by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER.

**Features:**
* **`culmen_length_mm`**: Length of the dorsal ridge of the bird's bill.
* **`culmen_depth_mm`**: Depth of the bill.
* **`flipper_length_mm`**: Length of the flipper.
* **`body_mass_g`**: Body mass in grams.
* **`sex`**: The gender of the penguin.

## Methodology

### 1. Data Preprocessing
To prepare the data for the distance-based K-Means algorithm, several transformations were applied:
* **Encoding Categorical Data:** Converted the `sex` column into dummy/indicator variables (`sex_MALE`, `sex_FEMALE`) using `pd.get_dummies` to make it machine-readable.
* **Feature Scaling:** Applied `StandardScaler` to normalize the data. This ensures that features with larger ranges (like body mass) do not disproportionately influence the clustering algorithm.

### 2. Determining Optimal Clusters (Elbow Method)
To find the ideal number of groups, the analysis utilized the **Elbow Method**:
* Iterated through a range of 1 to 10 clusters ($k$).
* Calculated the **inertia** (within-cluster sum of squares) for each $k$.
* Visualized the results to identify the "elbow" point where diminishing returns begin.


*Based on the analysis, **4 clusters** were selected as the optimal number for this specific dataset configuration.*

### 3. Model Application & Analysis
* **Clustering:** Applied the `KMeans` algorithm with `n_clusters=4` to the preprocessed data.
* **Visualization:** Plotted the resulting clusters to visually assess the separation based on culmen length.
* **Statistical Summary:** Created a summary DataFrame (`stat_penguins`) grouped by the new cluster labels to analyze the average physical characteristics of each identified group.


## Results
The model successfully identified 4 distinct groups with the following average characteristics:

| Cluster | Culmen Length (mm) | Culmen Depth (mm) | Flipper Length (mm) |
| :--- | :--- | :--- | :--- |
| **0** | ~43.88 | ~19.11 | ~194.76 |
| **1** | ~40.22 | ~17.61 | ~189.05 |
| **2** | ~49.47 | ~15.72 | ~221.54 |
| **3** | ~45.56 | ~14.24 | ~212.71 |

*Data derived from the final groupby analysis.*

## Technologies Used
* **Python**: Core programming language.
* **pandas**: Data manipulation and aggregation.
* **matplotlib**: Visualization (Elbow plot and Cluster scatter plot).
* **scikit-learn**: Machine learning workflows (`StandardScaler`, `KMeans`).

## Usage
1.  Ensure `penguins.csv` is located in the root directory.
2.  Run the Jupyter Notebook.
3.  The notebook will display the Elbow plot, the Cluster visualization, and output the summary statistics for the identified groups.
