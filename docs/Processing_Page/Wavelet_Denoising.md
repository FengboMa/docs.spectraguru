---
layout: default
title: Wavelet Denoising
parent: Smoothening
grand_parent: Processing Feature
permalink: /docs/Processing_Page/Processing_Feature/Smoothening/Wavelet_Denoising/
nav_order: 4
---

# Wavelet Denoising
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Wavelet Denoising reduces spectral noise by decomposing a spectrum into wavelet coefficients, shrinking high-frequency detail coefficients, and reconstructing the signal.

## How to use

1. Upload data, then open **Processing Page**.
2. Enable **Smoothening**.
3. In **Select your smoothening function**, choose **Wavelet Denoising**.
4. Choose **Wavelet denoising method**, **Wavelet family**, and **Decomposition level**.
5. For **Sardy Block Coordinate Relaxation(BCR)**, set **BCR iterations** and **Robust loss function**.
6. For **Standard Universal Thresholding**, set **Thresholding mode**.
7. Apply the processing workflow to update the spectra.

## Behavior

Wavelet denoising decomposes each spectrum into wavelet coefficients, shrinks high-frequency detail coefficients, and reconstructs a smoother spectrum. Standard Universal Thresholding is a single-pass denoising method. Sardy BCR is an iterative robust method that reduces the effect of large residuals while refining detail coefficients.

## Method

Standard mode estimates noise from the finest detail coefficients and applies a universal threshold:

$$\lambda = \hat{\sigma}\sqrt{2\log(n)}$$

Sardy BCR scales the same threshold and iteratively updates residual weights:

$$\lambda_{\text{BCR}} = s_{\lambda}\hat{\sigma}\sqrt{2\log(n)}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Wavelet denoising method | Tunable | `Sardy Block Coordinate Relaxation(BCR)` or `Standard Universal Thresholding`; default Sardy BCR |
| Wavelet family | Tunable | `sym4`, `sym8`, `db4`, `db8`, `coif1`, `coif3`, `haar`; default `sym4` |
| Decomposition level | Tunable | `1`-`6`; UI default `4`; internally clipped to the maximum valid level |
| BCR iterations | Tunable | `1`-`15`; default `10` |
| Robust loss function | Tunable | `huber` or `l1`; default `huber` |
| Thresholding mode | Tunable | `soft` or `hard`; default `soft` |
| Huber delta | Fixed | `1.5` in the Sardy BCR helper |
| Lambda scale | Fixed | `1.0` in the Sardy BCR helper |

## References

1. Sardy, S., Tseng, P., & Bruce, A. (2001). Robust wavelet denoising. https://www.unige.ch/~sardy/Papers/robustIEEE.pdf
2. Donoho, D. L., & Johnstone, I. M. (1994). Ideal spatial adaptation by wavelet shrinkage. *Biometrika*, 81(3), 425-455. https://doi.org/10.1093/biomet/81.3.425
3. PyWavelets Developers. PyWavelets documentation. https://pywavelets.readthedocs.io/
