# Wholesale Customers — Intro to Machine Learning Final Project

## Dataset overview

This dataset describes **440 customers of a wholesale distributor**. Each row represents one customer, with annual spending across six product categories and two categorical variables describing the customer.

- **Source:** [UCI Machine Learning Repository — Wholesale Customers](https://archive.ics.uci.edu/dataset/292/wholesale+customers)
- **File:** `Wholesale customers data.csv`
- **Columns:** 8 (6 numerical spending variables and 2 categorical variables).
- **Missing values:** None reported by UCI; verify this when loading the data.
- **Units:** Spending is expressed in monetary units (m.u.); do not assume a specific currency.

## Variables

| Variable | Type | What it contains |
| --- | --- | --- |
| `Channel` | Categorical | Customer business channel: `1` = Horeca (hotel, restaurant, or café); `2` = retail. |
| `Region` | Categorical | Customer region: `1` = Lisbon; `2` = Oporto; `3` = other region. |
| `Fresh` | Numerical | Annual spending on fresh products, in m.u. |
| `Milk` | Numerical | Annual spending on milk products, in m.u. |
| `Grocery` | Numerical | Annual spending on grocery products, in m.u. |
| `Frozen` | Numerical | Annual spending on frozen products, in m.u. |
| `Detergents_Paper` | Numerical | Annual spending on detergents and paper products, in m.u. |
| `Delicassen` | Numerical | Annual spending on delicatessen products, in m.u. |

Keep the CSV spelling `Delicassen` in your code. Spending values are stored as integers but represent amounts, not product counts. `Channel` and `Region` are category codes, not numerical measurements.

## Final project objective

Apply the final-project workflow to investigate:

> Can customers be grouped into meaningful segments based on their annual purchasing patterns?

Use the six spending variables to discover groups. Keep `Channel` and `Region` separate from the clustering inputs and use them afterward to describe the groups. A cluster does not have to correspond to either category.

## Expected work

1. **Explore the data.** Inspect dimensions, types, missing values, duplicate rows, distributions, correlations, and unusual spending values. Explain cleaning decisions; identical spending records are not automatically duplicate customers.
2. **Prepare the features.** Explain your scaling strategy. Consider a `log1p` transformation for skewed spending distributions and justify any treatment of outliers.
3. **Compare two methods.** Apply K-means and hierarchical clustering. Test several cluster counts and explain the distance metric and linkage used for hierarchical clustering.
4. **Evaluate the results.** Use silhouette scores, K-means inertia/elbow plots, and cluster sizes and interpretability to support your choices. Calculate comparable scores using the same feature representation and distance metric. Explain disagreements between methods.
5. **Use PCA if useful.** Visualize customers in two principal components and report the explained variance. State whether PCA is only used for visualization or also changes the clustering inputs. A 2D plot may hide differences present in the full feature space.
6. **Interpret the segments.** Summarize each cluster using spending statistics in the original monetary units. Give evidence-based descriptions, compare channel/region distributions, and suggest how a distributor could use the findings.

## Questions to discuss

- Which spending categories distinguish the segments?
- Are the groups mainly driven by total spending or by the mix of products purchased?
- How sensitive are the results to scaling, outliers, and the number of clusters?
- Do the segments relate to customer channel or region?
- What limitations prevent these findings from generalizing to other customers?

## Deliverables

Following the final-project format, submit:

- A reproducible Python notebook with code, plots, preprocessing decisions, model comparisons, and conclusions. Set random seeds where applicable and include package versions or a requirements file.
- A **3–4-page report** explaining the question, methods, evaluation, findings, and limitations.
- A **5–7-minute presentation** of the main findings.

The goal is a justified analysis, not a predetermined number of clusters or a required score. Do not treat cluster IDs as ground-truth labels or report classification accuracy for clustering.

## Attribution

Cardoso, M. (2013). *Wholesale customers* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5030X.

Dataset license: **Creative Commons Attribution 4.0 International (CC BY 4.0)**.
