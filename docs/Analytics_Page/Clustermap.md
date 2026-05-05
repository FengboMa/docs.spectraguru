---
layout: default
title: HCA
parent: Machine Learning Feature
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Clustermap/
nav_order: 3
---

# Hierarchical Cluster Analysis (HCA)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Hierarchical Cluster Analysis (HCA) groups spectra by similarity and displays the result as a clustered heatmap or dendrogram. In SpectraGuru, this feature uses Ward-linkage clustering to arrange similar spectra near each other.

## How to use

1. Upload data and finish preprocessing if needed.
2. Open **Analytics Page**.
3. In **Select Analytics Plot**, choose **Hierarchically-clustered Heatmap**.
4. Use **Show clustered heatmap** to switch between the clustered heatmap and dendrogram-only view.

## Behavior

When the heatmap toggle is enabled, SpectraGuru displays spectra as a heatmap ordered by hierarchical clustering, with a dendrogram showing the merge order. When the toggle is disabled, SpectraGuru shows the dendrogram with Ward distance on the vertical axis.

## Method

The default distance between spectra is Euclidean:

$$d(x,y)=\sqrt{\sum_i (x_i-y_i)^2}$$

Ward linkage merges clusters to minimize within-cluster variance:

$$\Delta(A,B)=\frac{|A||B|}{|A|+|B|}\lVert \bar{x}_A-\bar{x}_B\rVert^2$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Show clustered heatmap | Tunable | Boolean toggle, default `True` |
| Linkage method | Fixed | Ward linkage |
| Heatmap output | Fixed | Clustered heatmap when enabled; dendrogram view when disabled |

## References

1. Ward, J. H. Jr. (1963). Hierarchical grouping to optimize an objective function. *Journal of the American Statistical Association*, 58(301), 236-244. https://doi.org/10.1080/01621459.1963.10500845
2. SciPy Developers. `scipy.cluster.hierarchy.linkage`. https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.linkage.html
3. Waskom, M. L. (2021). Seaborn: statistical data visualization. *Journal of Open Source Software*, 6(60), 3021. https://doi.org/10.21105/joss.03021
