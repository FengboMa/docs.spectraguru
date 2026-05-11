---
layout: default
title: Random Forest(RF) Classification
parent: Machine Learning Feature
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Machine_Learning_Feature/Random_Forest_Classification/
nav_order: 4
---

# Random Forest(RF) Classification
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Random Forest(RF) is a supervised ensemble classifier that trains multiple decision trees and combines their class votes.

## How to use

1. Upload data and assign labels on **Data Upload**. Classification requires labels for every selected spectrum and at least two classes.
2. Finish preprocessing, then open **Analytics Page**.
3. In **Select Analytics Plot**, choose **Random Forest(RF) Classification**.
4. Set **Number of Trees**, **Maximum Tree Depth**, **Minimum Samples per Leaf**, and **Test Size (%)** in the sidebar form.
5. Click **Run Random Forest**.

## Behavior

SpectraGuru trains a random forest on the selected spectra after dropping the generated **Average** column. If **Test Size (%)** is `0`, the model is fitted and evaluated on the full selected dataset. If the test size is greater than `0`, SpectraGuru makes a stratified train/test split and reports both training and test results. The page shows class counts by split, class balance, class spectra envelopes, a performance table, confusion matrix, and one-vs-rest ROC curves.

## Method

The spectra matrix is transposed so samples are rows and Raman shift intensities are features, then standardized:

$$z = \frac{x-\mu}{\sigma}$$

Each tree votes for a class, and the forest prediction is the majority vote:

$$\hat{y} = \operatorname{mode}\{T_1(x), T_2(x), \ldots, T_B(x)\}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Number of Trees | Tunable | `n_estimators`, default `100`, range `1`-`500` |
| Maximum Tree Depth | Tunable | `0` means unlimited depth; otherwise passed as `max_depth` |
| Minimum Samples per Leaf | Tunable | `min_samples_leaf`, default `1` |
| Test Size (%) | Tunable | `0`-`80`; `0` uses the full dataset for fit and evaluation |
| Split random state | Fixed | `42` |
| Split strategy | Fixed | Stratified by label when test size is greater than `0` |
| Feature scaling | Fixed | `StandardScaler` before fitting |
| `max_features` | Fixed | `"sqrt"` |
| Criterion | Fixed | `"gini"` |
| Bootstrap | Fixed | `True` |

## References

1. Breiman, L. (2001). Random forests. *Machine Learning*, 45, 5-32. https://doi.org/10.1023/A:1010933404324
2. Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, E. (2011). Scikit-learn: Machine Learning in Python. *Journal of Machine Learning Research*, 12, 2825-2830. https://doi.org/10.48550/arXiv.1201.0490
3. Scikit-learn Developers. `RandomForestClassifier`. https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html
