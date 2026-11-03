# Homework: explore and cluster wines with K-means

Use [`wine-clustering.csv`](wine-clustering.csv) to find groups of wines from their chemical measurements. The file has 178 wines, 13 numeric features, and **no known group labels**. Work in a notebook or Python script and keep your explanation short and evidence based.

## What the columns mean

| Column | Meaning |
| --- | --- |
| `Alcohol` | Alcohol content of the wine. |
| `Malic_Acid` | Amount of malic acid, an organic acid that affects tartness. |
| `Ash` | Mineral residue left after the wine is burned. |
| `Ash_Alcanity` | Alkalinity of that ash (the dataset uses this spelling). |
| `Magnesium` | Amount of magnesium. |
| `Total_Phenols` | Total amount of phenolic compounds. |
| `Flavanoids` | Amount of flavonoid phenolic compounds. |
| `Nonflavanoid_Phenols` | Amount of phenolic compounds that are not flavonoids. |
| `Proanthocyanins` | Amount of proanthocyanins, a type of phenolic compound. |
| `Color_Intensity` | Strength of the wine's color. |
| `Hue` | Shade of the wine's color. |
| `OD280` | OD280/OD315 measurement of diluted wine, related to its phenolic composition. |
| `Proline` | Amount of the amino acid proline. |

The CSV does not provide measurement units, so do not assume units when interpreting values.

## Your tasks

1. **Explore the data.** Load the CSV; report its shape, missing values, duplicate rows, and each column's minimum, maximum, mean, and standard deviation. Plot the feature distributions and inspect a correlation heatmap or a few scatterplots. Describe two patterns or unusual values you notice.
2. **Decide what to scale.** Compare the feature ranges. Explain which columns you would scale and which, if any, you would leave unscaled. All 13 columns are numeric measurements, but they have very different ranges: `Proline` runs from 278 to 1680, while `Hue` runs from 0.48 to 1.71. For the main K-means analysis, standardize **all 13 features** (subtract each column's mean and divide by its standard deviation). Briefly explain how leaving them unscaled could change the clusters.
3. **Try different K values.** Fit K-means to the standardized data for K=1 through 10. Keep the same preprocessing and use `random_state=42` and `n_init=10` so your results are reproducible. Record each model's inertia (within-cluster sum of squares).
4. **Use the elbow method.** Plot inertia against K. Choose a K where adding another cluster begins to give much smaller improvements. The elbow is a judgment, not a guaranteed correct answer; explain your choice using the plot.
5. **Interpret the clusters.** Refit K-means with your chosen K. Report the number of wines in each cluster and the mean of each **original, unscaled** feature within each cluster. Describe at least two differences between the groups. Cluster numbers are arbitrary and do not represent quality ratings or known wine types.

Submit your notebook or script with the plots and a short written answer covering your scaling decision, elbow choice, and cluster interpretation.

## Example insight from this dataset

With all columns standardized and the settings above, inertia drops from **2314** at K=1 to **1659** at K=2 and **1278** at K=3; the next step to K=4 reaches **1175**. This makes **K=3 a reasonable elbow choice**, although another choice can be defended from the plot. The three clusters contain **65, 51, and 62 wines**.

In this K=3 run, one group has lower average `Proline` (about 510) and `Color_Intensity` (2.97). Another has higher `Malic_Acid` (3.31) and `Color_Intensity` (7.23), but lower `Flavanoids` (0.82). The third has higher `Proline` (1100), `Flavanoids` (3.00), and `Alcohol` (13.68). These are descriptive patterns in the measurements; without labels, they do not establish the wines' origin or quality.
