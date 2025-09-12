---
layout: default
title: Clustermap
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Clustermap/
nav_order: 6
---

# Hierarchically-clustered Heatmap
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

Hierarchical clustering seeks to group samples based on their similarity to each other, organizing them into multiple categories that can be used for further analysis. Samples are grouped together one at a time and a graph is displayed showing which samples combined and in which order. The user has the option to view a heatmap that provides a colorful visualization of the data from each sample, arranged to bring out the contrast between data in distant groups.

## How to Use

0. In the analytics page, after processing your data, select “Hierarchically-clustered Heatmap” from the drop-down menu on the left sidebar.
1. Select whether you would like to see a colored heatmap of your data using the toggle labeled “Show clustered heatmap.” By default, this option is turned on. If turned off, a plot of the Ward distances between clustered spectra will be made visible instead.
2. The colored heatmap renders the spectra vertically, so that the Raman shift is arranged on the right of the plot and each sample is laid out side by side. The intensity is graphed using color at each Raman shift value. To the left of the plot, a key is displayed explaining the color scheme used: 
    - Dark, blue colors represent low intensities. 
    - Light, yellow colors represent higher intensities.
3. Above the heatmap is a tree that shows how the samples were grouped together during the clustering process. This type of tree is also known as a dendrogram. Read from the bottom upwards, each conjunction represents the two next most similar groups being paired together. See additional information about this dendrogram in the next section.
4. You can view the specific similarity values between each group by turning off the “Show clustered heatmap” toggle. In this view, only the hierarchy tree is visible, but it is labeled with the Ward distance between each group on the vertical axis.

## Behavior

- Ward's Method: SpectraGuru uses Ward’s method to group samples together by their similarity. This is a recursive algorithm that repeatedly updates the “distances” between groups of samples and merges the two groups with the least distance between them. When two groups are merged, they are henceforth treated as a single group by the algorithm. The goal of Ward’s method is to minimize the total variance within each group at each step. The details of the algorithm are as follows:
    0. The initial distance between each sample is the Euclidean distance between them. Each sample can be thought of as a vector in an $n$-dimensional space, where $n$ is the number of rows in the data (i.e. the number of different Raman shift values observed). The Euclidean distance $E$ between two samples $A$ and $B$ is defined as follows:

        $$
        E(A, B)=\sqrt{\sum_x {\left(B(x)-A(x)\right)}^2}
        $$
    
        where $A(x)$ and $B(x)$ represent the intensities of samples $A$ and $B$ at Raman shift $x$.
    1. For the next iteration, Ward's method merges the two samples with the least distance between them into a single group $u$, and then updates that group's distance to each other sample using the following formula:

        $$
        D(u, v)=\sqrt{\frac{|v|+|s|}{T} {D(v, s)}^2 + \frac{|v|+|t|}{T} {D(v, t)}^2 - \frac{|v|}{T} {D(s, t)}^2}
        $$
    
        where $u$ is the newly formed group, $s$ and $t$ are the two groups that merged to form $u$, and $v$ is any other group. $D(x, y)$ is the Ward distance between groups $x$ and $y$ (this is just the Euclidean distance if the groups are still single samples), $|x|$ is the number of samples in group $x$, and $T=|v|+|s|+|t|$.
    2. After finding the new distances, the two groups with the smallest distance are again chosen to be merged, and the distances are updated again using the formula above. This process repeats until all samples are combined into a single group.
- Colored heatmap: If the “Show clustered heatmap” toggle is turned on, a heatmap of the data is displayed such that each sample is laid out side by side, and the vertical axis represents Raman shift (lower frequencies towards the top). Intensities are visualized using color. The samples are ordered such that they appear next to samples they are similar to. Above the plot, a dendrogram is drawn that shows how each sample was merged into groups with each other.
- Dendrogram view: If the “Show clustered heatmap” toggle is turned off, the dendrogram created during clustering is enlarged, and the Ward distances at each step are plotted on the vertical axis. The “Ward distance” refers to the distance between the two merged groups at each step. Large jumps in the Ward distance from one step to another indicate that the two merged groups were not very similar to each other. Likewise, smaller jumps in the Ward distance indicate that the two groups were relatively similar.

## References

SpectraGuru uses Seaborn's [`clustermap`](https://seaborn.pydata.org/generated/seaborn.clustermap.html) function to visualize hierarchically-clustered data. Ward's method is implemented by Scipy's [`linkage`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.linkage.html#scipy.cluster.hierarchy.linkage) function.

1. Waskom, M. L. (2021). Seaborn: statistical data visualization. Journal of Open Source Software, 6(60), 3021. https://doi.org/10.21105/joss.03021

2. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17(3), 261–272. https://doi.org/10.1038/s41592-019-0686-2

3. Ward, J. H. Jr. (1963). Hierarchical grouping to optimize an objective function. Journal of the American Statistical Association, 58(301), 236–244. https://doi.org/10.1080/01621459.1963.10500845
