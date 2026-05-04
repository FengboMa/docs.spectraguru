---
layout: default
title: KNN Classification
parent: Machine Learning Feature
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Machine_Learning_Feature/KNN_Classification/
nav_order: 5
---

# K-Nearest Neighbors(KNN) Classification
{: .no_toc }

## How to use

1. Upload data and assign labels on **Data Upload**. Classification requires labels for every selected spectrum and at least two classes.
2. Finish preprocessing, then open **Analytics Page**.
3. In **Select Analytics Plot**, choose **K-Nearest Neighbors(KNN) Classification**.
4. Set **Number of Neighbors (K)**, **Weights**, **Distance Metric**, and **Test Size (%)** in the sidebar form.
5. Click **Run KNN**.

## Behavior

SpectraGuru classifies each spectrum by comparing it with nearby labeled spectra in standardized intensity-feature space. If **Test Size (%)** is `0`, the page reports full-dataset performance. If test size is greater than `0`, the page reports training and test split composition, class balance, spectra envelopes, macro-averaged metrics, confusion matrices, and one-vs-rest ROC curves.

## Method

The selected spectra are standardized before distance calculations:

$$z = \frac{x-\mu}{\sigma}$$

For a sample $x$, KNN predicts the class most supported by its neighbor set $\mathcal{N}_K(x)$:

$$\hat{y} = \arg\max_c \sum_{i \in \mathcal{N}_K(x)} w_i I(y_i=c)$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Number of Neighbors (K) | Tunable | `n_neighbors`, default `3`, range `1`-`100` |
| Weights | Tunable | `uniform` or `distance`; default `uniform` |
| Distance Metric | Tunable | `euclidean`, `manhattan`, or `minkowski`; default `euclidean` |
| Test Size (%) | Tunable | `0`-`80`; `0` uses the full dataset for fit and evaluation |
| Split random state | Fixed | `42` |
| Split strategy | Fixed | Stratified by label when test size is greater than `0` |
| Feature scaling | Fixed | `StandardScaler` before fitting |

## References

1. Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, E. (2011). Scikit-learn: Machine Learning in Python. *Journal of Machine Learning Research*, 12, 2825-2830. https://doi.org/10.48550/arXiv.1201.0490
2. Scikit-learn Developers. `KNeighborsClassifier`. https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html
