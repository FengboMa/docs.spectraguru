---
layout: default
title: T-SNE
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/T-SNE/
nav_order: 8
---

# T-distributed Stochastic Neighbor Embedding (t-SNE)
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

T-Distributed Stochastic Neighbor Embedding (t-SNE) is a dimensionality reduction algorithm that preserves the clustering of high-dimensional data. In other words, T-SNE is a way to visualize data that cannot be plotted traditionally in two or three dimensions. This is useful for understanding which samples are most similar to each other. However, unlike PCA, t-SNE generally produces plots where the axes do not encode any meaningful information on their own, since the focus is simply to preserve the relative distance between data points.

## How to Use

0. In the analytics page, after processing your data, select “T-SNE Dimensionality Reduction” from the drop-down menu on the left sidebar.
1. Use the slider labeled “t-SNE Perplexity” to set the perplexity used by the t-SNE algorithm.
2. Use the slider labeled “t-SNE Maximum number of iterations” to set the maximum number of iterations the t-SNE algorithm performs before stopping. This can be useful for large data sets which may be computationally expensive to process.
3. The plot labeled “t-SNE Visualization” is a projection of all of your samples into 2 dimensions. The horizontal and vertical axes do not encode any meaningful information; instead, the plot is a visualization tool meant to separate the samples into different clusters based on their similarity.

## Definitions

- $\lvert\lvert A-B\rvert\rvert$ denotes the *Euclidean distance* between samples $A$ and $B$ (see the [hierarchically-clustered heatmap](/docs.spectraguru/docs/Analytics_Page/Analytics_Features/Clustermap/) documentation for how Euclidean distance is defined)
- A *Gaussian distribution* is a probability distribution also known as a normal distribution or a "bell curve," expressed mathematically as $e^{-t^2/(2\sigma^2)}$, where $\sigma$ is the standard deviation of the distribution.
- The *scaled similarity* between a sample $A_i$ and another sample $A_j$ is based on the normalized Gaussian distribution of their distance compared to all other points, defined by:
    
    {% raw %}
    $$
    s(i, j)=\frac{e^{-{\lvert\lvert A_i-A_j\rvert\rvert}^2/(2{{\sigma}_i}^2)}}{\sum_{k \neq i} \left(e^{-{\lvert\lvert A_i-A_k\rvert\rvert}^2/(2{{\sigma}_i}^2)}\right)}
    $$
    {% endraw %}

    where $\sigma_i$ is the standard deviation for sample $A_i$, selected to universalize the *perplexity* chosen by the user (see the next paragraph on perplexity).
- *Perplexity* is a measure of the size of clusters in a data set. Data sets with large clusters have higher perplexity, while data sets with small, numerous clusters have lower perplexity. However, perplexity is a little subjective and is never calculated explicitly. Its value is guessed by the user (values between `5` and `50` typically yield the best results) and then used to determine the standard deviations for each point’s Gaussian distribution using the following formula: 

    $$
    P=2^{-\sum_{j \neq i} s(i, j)\log_2 s(i, j)}
    $$

    where $P$ is the perplexity, and s(i, j) is the scaled similarity between samples $A_i$ and $A_j$. This formula is used to solve for the standard deviation $\sigma_i$ of the Gaussian distribution around $A_i$ that satisfies the equation. A low perplexity should be chosen if the user wants data to be grouped into fine categories, and a higher perplexity should be chosen for broader categories.
- *T-distributed similarity* is like the standard similarity, but instead of using a Gaussian distribution, a *Student's t-distribution* is used. The t-distribution used by this algorithm is expressed as $\frac{1}{1+t^2}$, and it looks like a shorter version of the Gaussian bell curve with higher edges. The t-distributed similarity $t(i, j)$ between two samples $Q_i$ and $Q_j$ is defined as:

    {% raw %}
    $$
    t(i, j)=\frac{{\left(1+{\lvert\lvert Q_i-Q_j\rvert\rvert}^2\right)}^{-1}}{\sum_{k \neq i} {\left(1+{\lvert\lvert Q_i-Q_k\rvert\rvert}^2\right)}^{-1}}
    $$
    {% endraw %}

- *Kullback-Leibler divergence* is a way of measuring how much two probability distributions differ. By treating the similarity values of the true data and projected data as probability distributions, we can use Kullback-Leibler divergence to quantify how accurate the current model is. You can think of the “probabilities” corresponding to the similarity values as the probabilities of two points being part of the same cluster. Kullback-Leibler divergence is denoted by $D_{KL}(P \vert\vert Q)$ and is defined by:
    
    {% raw %}
    $$
    D_{KL}(P \vert\vert Q)=\sum_{x}P(x)log\left(\frac{P(x)}{Q(x)}\right)
    $$
    {% endraw %}

    where $P$ and $Q$ are probability distributions.
- *Gradient descent* is a minimization algorithm that calculates the gradient vector of a function at a particular input and takes a step in the opposite direction to determine the next input, since the gradient vector points in the direction where the function increases the fastest. This will be used to minimize the Kullback-Leibler divergence mentioned above.

## Behavior

- Algorithm: SpectraGuru uses Scikit-learn's [`TSNE`](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html) class to analyze your data. The algorithm for this analysis works as follows:
    0. Find the Euclidean distances between each pair of samples.
    1. For each sample $A_i$, test different values of $\sigma_i$ until one is found that satisfies the perplexity formula. This is done using binary search.
    2. For each sample $A_i$, use the corresponding $\sigma_i$ to calculate the similarities $s(i, j)$ between it and each other sample $A_j$.
    3. Randomly project each sample onto a 2-dimensional space (called the *embedding space*) for visualization.
    4. For each projected sample $Q_i$. find the t-distributed similarities $t(i, j)$ between it and each other projected sample $Q_j$.
    5. After finding all the similarities $s(i, j)$ and projected similarities $t(i, j)$, treat $s$ and $t$ as two probability distributions and compare them using Kullback-Leibler divergence. This results in a very high-dimensional function $D_{KL}(s \vert\vert t)$.
    6. Minimize $D_{KL}(s \vert\vert t)$ by using gradient descent, where the embedding space varies. This will take multiple iterations, and each projected point $Q$ as well as the new t-distribution $t(i, j)$ will have to be updated after each iteration, meaning this process is somewhat computationally expensive. The process stops when either a minimum is found (i.e. the length of the gradient vector is close to `0`) or the maximum number of iterations is reached.
    7. The output of this algorithm is the 2-dimensional embedding space (i.e the set of projected points $Q$) representing your data after the final iteration of gradient descent.
- User control: The user controls both the perplexity and maximum number of iterations by adjusting the sliders located on the left sidebar. The perplexity ranges from `1` to `N-1`, where `N` is the number of samples. The maximum number of iterations ranges from `200` to `1000`.

## References

SpectraGuru uses the [`TSNE`](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html) class from Scikit-learn to perform dimensionality reduction.

1. Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., ... Duchesnay, É. (2011). Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, 12, 2825–2830.

2. van der Maaten, L., & Hinton, G. (2008). *Visualizing Data using t-SNE*. Journal of Machine Learning Research, 9, 2579–2605. https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf
