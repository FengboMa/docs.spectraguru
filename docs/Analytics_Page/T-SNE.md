---
layout: default
title: t-SNE
parent: Machine Learning Feature
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/T-SNE/
nav_order: 2
---

# T-distributed Stochastic Neighbor Embedding (t-SNE)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

T-distributed Stochastic Neighbor Embedding (t-SNE) is a nonlinear dimensionality-reduction algorithm for visualizing high-dimensional spectra in two dimensions. It is useful for inspecting local grouping patterns, but its axes do not have direct physical meaning.

## How to use

1. Upload data and finish preprocessing if needed.
2. Open **Analytics Page**.
3. In **Select Analytics Plot**, choose **T-SNE Dimensionality Reduction-Beta**.
4. Set **t-SNE Perplexity**.
5. Set **t-SNE Maximum number of iterations**.

## Behavior

SpectraGuru displays a two-dimensional t-SNE visualization of the selected spectra. Nearby points represent spectra that the algorithm placed close together in the embedding. If labels are available from Data Upload, they are used for coloring.

## Method

t-SNE minimizes the divergence between neighbor probabilities in the original space and the two-dimensional embedding:

$$D_{KL}(P\Vert Q)=\sum_{i,j}p_{ij}\log\frac{p_{ij}}{q_{ij}}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| t-SNE Perplexity | Tunable | Slider from `1` to `N-1`; default `2` |
| t-SNE Maximum number of iterations | Tunable | Slider `200`-`1000`; default `500` |
| Output dimensions | Fixed | 2D embedding |
| t-SNE implementation | Fixed | `sklearn.manifold.TSNE` |

## References

1. van der Maaten, L., & Hinton, G. (2008). Visualizing data using t-SNE. *Journal of Machine Learning Research*, 9, 2579-2605. https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf
2. Scikit-learn Developers. `TSNE`. https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html
