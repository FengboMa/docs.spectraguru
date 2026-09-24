---
layout: default
title: Principal Components Analysis (PCA)
parent: Machine Learning Feature
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Principal_Component_Analysis/
nav_order: 2
---

# Principal Components Analysis (PCA)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Principal Components Analysis (PCA) is a dimensionality-reduction algorithm that projects spectra onto orthogonal components that capture major variance patterns. In SpectraGuru, PCA helps users inspect sample separation, explained variance, and loading patterns.

## How to use

1. Upload data and finish preprocessing if needed.
2. Open **Analytics Page**.
3. In **Select Analytics Plot**, choose **Principal Components Analysis (PCA)**.
4. Use **Select horizontal PC** and **Select vertical PC** to choose the scatter plot axes.
5. Use the available **PC1 loading curve**, **PC2 loading curve**, and **PC3 loading curve** checkboxes to choose which loading curves to show. All available curves are selected by default.

## Behavior

SpectraGuru displays a two-dimensional PCA score plot, a cumulative explained variance plot, and a **PCA Scores by Spectrum** table. Scores are colored by their uploaded labels; if no label table is available, every spectrum is assigned the same default label. The loading plot shows the selected curves from the first three available components. If no loading curves are selected, that plot is hidden while the scores and variance plots remain.

## Method

SpectraGuru scales the spectra before PCA:

$$Z=\frac{X-\mu}{\sigma}$$

The displayed scores are projections onto principal component directions:

$$T=ZW$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Select horizontal PC | Tunable | Principal component shown on the x-axis |
| Select vertical PC | Tunable | Principal component shown on the y-axis |
| PC1–PC3 loading curves | Tunable | Up to three available components; all selected by default |
| Label coloring | Fixed | Scores are colored by label |
| Scaling | Fixed | Standard scaling before PCA |
| PCA implementation | Fixed | `sklearn.decomposition.PCA` |

## References

1. Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, E. (2011). Scikit-learn: Machine Learning in Python. *Journal of Machine Learning Research*, 12, 2825-2830. https://doi.org/10.48550/arXiv.1201.0490
2. Scikit-learn Developers. `PCA`. https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html
