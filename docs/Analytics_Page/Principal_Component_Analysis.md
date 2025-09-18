---
layout: default
title: Principal Component Analysis
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Principal_Component_Analysis/
nav_order: 7
---

# Principal Component Analysis (PCA)
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

Principal Component Analysis (PCA) is a way of boiling your data down to a small list of features without sacrificing accuracy. It does this by analyzing trends in the data and using those trends to define *principal components* which should encapsulate the underlying causes of those trends. This is an essential tool for identifying noise, finding key differences between samples, and reducing the redundancy of your data, which helps to extract the most important details for analysis.

## Definitions

- A *principal component* can be thought of as a vector in a high-dimensional space that points in a meaningful direction through your data. Principal components are designed to maximize the variance of the data projected onto them, and they must be perpendicular to each other (i.e. they make right angles with each other).
- *Variance* quantifies how far, on average, a set of data deviates from its mean. Mathematically, the variance $s^2$ of a collection of points $x$ is defined by:

    $$
    s^2=\frac{1}{n-1} \sum_{i=1}^n {|x_i-\bar{x}|}^2
    $$

    where $n$ is the number of data points in $x$, and $\bar{x}$ is the mean of the data.
- The *loading score* of a variable for a given principal component quantifies the contribution of that variable to the unit principal component vector (also known as the *singular vector*). Mathematically, the loading score for variable $x_k$ is the $k^{th}$ entry of the singular vector.

## How to Use

0. In the analytics page, after processing your data, select “Principal Component Analysis (PCA)” from the drop-down menu on the left sidebar.
1. The first plot is a scatterplot where each point represents one of your samples, and each axis represents a principal component of your data. To keep the plot 2-dimensional, only two principal components can be analyzed at a time. You can select which two principal components to analyze using the drop-down menus labeled “Select Horizontal PC” and “Select Vertical PC.”
2. The second plot shows the *cumulative explained variance* as principal components are adopted from left to right. Keep in mind that principal components are ranked by dominance, with “PC1” contributing the most to the variance seen in the data.
    - *Cumulative explained variance* can be roughly summarized as the “resemblance to the original data if only the first $n$ principal components are used.”
3. The third plot graphs the loading scores for the first 3 principal components. Loading scores represent the relative importance of each original feature towards a given principal component. In this case, the original features are each recorded Raman shift value.
4. At the bottom of the page, a table is displayed which shows the principal features of each sample.

## Behavior

- PCA algorithm: SpectraGuru uses Scikit-learn’s [`PCA`](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) class to analyze your data. The number of components computed is equal to either the number of samples or the number of features, whichever is smaller. Before being processed, the data is scaled so that its mean is centered at zero and the variance is 1. Then, singular value decomposition is performed on the data matrix. The singular values found from this method are used to reconstruct the principal components.
- Scatterplot display: The PCA scatterplot plots all of the samples based on their principal features in two dimensions of your choice. You can select which principal components to use using the drop-down menus on the left sidebar. Principal components are sorted by explained variance, with `PC1` having the greatest explained variance.
- Cumulative explained variance: The “explained variance” of a single principal component is calculated by first projecting all the data onto the singular vector, finding the variance, and dividing by the original variance. This represents a portion of the total variance, so it must be between `0` and `1`. The cumulative explained variance at principal component $x$ is then simply the sum of the explained variance of each principal component up to and including $x$. Mathematically, the cumulative explained variance $C$ at principal component $P_k$ is defined as 

    $$
    C=\sum_{i=1}^k \left(\frac{s^2\left({proj}_{P_i}(X)\right)}{s^2(X)}\right)
    $$

    where $s^2(X)$ is the variance of data set $X$, $X$ is the original data, and ${proj}_{P_i}(X)$ is the projection of $X$ onto the singular vector of $P_i$.
- Loading scores: A graph of the loadings for the first three principal components is displayed below the plot of the cumulative explained variance. The horizontal axis represents the original features (each Raman shift value), and the vertical axis represents the loading score.

## References

SpectraGuru uses the [`PCA`](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) class from Scikit-learn to find principal components.

1. Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, É. (2011). Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, 12, 2825–2830.

2. Halko, N., Martinsson, P. G., & Tropp, J. A. (2011). Finding structure with randomness: Probabilistic algorithms for constructing approximate matrix decompositions. SIAM Review, 53(2), 217–288. https://doi.org/10.1137/090771806
