---
layout: default
title: Principal Component Analysis
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Principal_Component_Analysis/
nav_order: 7
---

# Hierarchically-clustered Heatmap
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
- *Variance* quantifies how far, on average, a set of data deviates from its mean. Mathematically, the variance ] of a collection of points ] is defined as ], where ] is the number of data points in ], and ] is the mean of the data.
- The *loading score* of a variable for a given principal component quantifies the contribution of that variable to the unit principal component vector (also known as the *singular vector*). Mathematically, the loading score for variable ] is the ] entry of the singular vector.

## How to Use

0. In the analytics page, after processing your data, select “Principal Component Analysis (PCA)” from the drop-down menu on the left sidebar.
1. The first plot is a scatterplot where each point represents one of your samples, and each axis represents a principal component of your data. To keep the plot 2-dimensional, only two principal components can be analyzed at a time. You can select which two principal components to analyze using the drop-down menus labeled “Select Horizontal PC” and “Select Vertical PC.”
2. The second plot shows the *cumulative explained variance* as principal components are adopted from left to right. Keep in mind that principal components are ranked by dominance, with “PC1” contributing the most to the variance seen in the data.
    - *Cumulative explained variance* can be roughly summarized as the “resemblance to the original data if only the first ] principal components are used.”
3. The third plot graphs the loading scores for the first 3 principal components. Loading scores represent the relative importance of each original feature towards a given principal component. In this case, the original features are each recorded Raman shift value.
4. At the bottom of the page, a table is displayed which shows the principal features of each sample.

## Behavior

- PCA algorithm: SpectraGuru uses Scikit-learn’s [`PCA`](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) class to analyze your data. The number of components computed is equal to either the number of samples or the number of features, whichever is smaller. Before being processed, the data is scaled so that its mean is centered at zero and the variance is 1. Then, singular value decomposition is performed on the data matrix. The singular values found from this method are used to reconstruct the principal components.
- Scatterplot display: The PCA scatterplot plots all of the samples based on their principal features in two dimensions of your choice. You can select which principal components to use using the drop-down menus on the left sidebar. Principal components are sorted by explained variance, with `PC1` having the greatest explained variance.
- Cumulative explained variance: The “explained variance” of a single principal component is calculated by first projecting all the data onto the singular vector, finding the variance, and dividing by the original variance. This represents a portion of the total variance, so it must be between `0` and `1`. The cumulative explained variance at principal component ] is then simply the sum of the explained variance of each principal component up to and including ]. Mathematically, the cumulative explained variance ] at principal component ] is defined as ], where ] is the variance of data set ], ] is the original data, and ] is the projection of ] onto the singular vector of ].
- Loading scores: A graph of the loadings for the first three principal components is displayed below the plot of the cumulative explained variance. The horizontal axis represents the original features (each Raman shift value), and the vertical axis represents the loading score.