---
layout: default
title: Support Vector Machine(SVM) Classification
parent: Machine Learning Feature
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Machine_Learning_Feature/SVM_Classification/
nav_order: 6
---

# Support Vector Machine(SVM) Classification
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Support Vector Machine(SVM) is a supervised classifier that separates labeled spectra using a margin-based decision boundary.

## How to use

1. Upload data and assign labels on **Data Upload**. Classification requires labels for every selected spectrum and at least two classes.
2. Finish preprocessing, then open **Analytics Page**.
3. In **Select Analytics Plot**, choose **Support Vector Machine(SVM) Classification**.
4. Set **Kernel**, **C**, **Class Weight**, **Polynomial Degree**, **Gamma**, and **Test Size (%)** in the sidebar form.
5. Click **Run SVM**.

## Behavior

SpectraGuru fits a probability-enabled support vector classifier on standardized spectra. The page reports class counts, class balance, class spectra envelopes, macro-averaged metrics, confusion matrices, and one-vs-rest ROC curves. With **Test Size (%)** set to `0`, the model is fitted and evaluated on the full dataset. With a nonzero test size, SpectraGuru uses a stratified train/test split.

## Method

The selected spectra are standardized before fitting:

$$z = \frac{x-\mu}{\sigma}$$

For a linear decision surface, SVM seeks a separating margin controlled by $C$:

$$\min_{w,b,\xi} \frac{1}{2}\lVert w\rVert^2 + C\sum_i \xi_i$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Kernel | Tunable | `RBF`, `Linear`, `Polynomial`, or `Sigmoid`; converted to scikit-learn kernel names |
| C | Tunable | Default `1.0`, range `0.01`-`100.0` |
| Class Weight | Tunable | `None` or `Balanced`; default `None` |
| Polynomial Degree | Tunable | Default `3`; used by the polynomial kernel |
| Gamma | Tunable | `scale` or `auto`; default `scale` |
| Test Size (%) | Tunable | `0`-`80`; `0` uses the full dataset for fit and evaluation |
| Split random state | Fixed | `42` |
| Split strategy | Fixed | Stratified by label when test size is greater than `0` |
| Feature scaling | Fixed | `StandardScaler` before fitting |
| Probability output | Fixed | `probability=True` so ROC curves are available for multiclass one-vs-rest evaluation |

## References

1. Cortes, C., & Vapnik, V. (1995). Support-vector networks. *Machine Learning*, 20, 273-297. https://doi.org/10.1007/BF00994018
2. Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, E. (2011). Scikit-learn: Machine Learning in Python. *Journal of Machine Learning Research*, 12, 2825-2830. https://doi.org/10.48550/arXiv.1201.0490
3. Scikit-learn Developers. `SVC`. https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html
