---
layout: default
title: ALS
parent: Baseline Removal
grand_parent: Processing Feature
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/ALS_Baseline_Removal/
nav_order: 4
---

# Asymmetric Least Squares (ALS)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Asymmetric Least Squares (ALS) is a baseline removal algorithm for estimating a smooth background beneath spectral peaks. SpectraGuru uses ALS when the user wants an adjustable smoothness penalty and asymmetric peak weighting.

## How to use

1. Upload data, then open **Processing Page**.
2. Enable **Baseline removal**.
3. In **Select baseline removal function**, choose **ALS**.
4. Set **ALS lambda**, **ALS asymmetry (p)**, **ALS difference order (d)**, and **ALS maximum iterations**.
5. Apply the processing workflow to subtract the estimated baseline.

## Behavior

ALS estimates a smooth baseline below the spectral peaks by repeatedly fitting a penalized least-squares curve and reweighting residuals. The result should reduce slow background drift while preserving sharper peaks for downstream analysis.

## Method

ALS solves a weighted smoothness-penalized least-squares problem:

$$\min_z \sum_i w_i(y_i-z_i)^2 + \lambda \lVert D_d z\rVert^2$$

Weights are updated asymmetrically so points above the baseline contribute less:

$$w_i = p \text{ if } y_i > z_i,\quad w_i = 1-p \text{ otherwise}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| ALS lambda | Tunable | Smoothness penalty; default `100`, UI range `1` to `1e10` |
| ALS asymmetry (p) | Tunable | Weighting asymmetry; default `0.001` |
| ALS difference order (d) | Tunable | Difference order `1`-`3`; default `1` |
| ALS maximum iterations | Tunable | Default `50`, UI range `1`-`200` |
| Linear solve | Fixed | Sparse solve of the weighted penalty system |

## References

1. Eilers, P. H. C., & Boelens, H. F. M. (2005). Baseline correction with asymmetric least squares smoothing. https://zanran_storage.s3.amazonaws.com/www.science.uva.nl/ContentPages/443199618.pdf
