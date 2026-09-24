---
layout: default
title: Normalization by Mean
parent: Normalization
grand_parent: Processing Feature
permalink: /docs/Processing_Page/Processing_Feature/Normalization/Normalization_Mean/
nav_order: 4
---

# Normalization by Mean
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Normalization by Mean rescales each spectrum by its own average intensity. It is useful when spectra should be compared relative to their typical signal level rather than their absolute intensity.

## How to use

1. Upload spectra and open **Processing Page**.
2. Turn on **Normalization** in the sidebar.
3. Choose **Normalize by mean** from **Select normalization function**.
4. Apply preprocessing and review the normalized spectra.

## Behavior

SpectraGuru calculates the arithmetic mean of all intensity values in each spectrum column, then divides that column by its own mean. The wavenumber axis is unchanged. There are no additional parameters for this normalization method. A spectrum needs a nonzero mean for the division to produce finite values.

## Method

For a spectrum with intensities $I_1,\ldots,I_N$, the normalized intensity at point $i$ is

$$I_i^{\mathrm{norm}}=\frac{I_i}{\bar I},\qquad \bar I=\frac{1}{N}\sum_{j=1}^{N}I_j.$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Normalization function | Tunable | Select **Normalize by mean** |
| Mean intensity | Fixed | Arithmetic mean calculated separately for each spectrum |
| Wavenumber axis | Fixed | Unchanged |

## References

1. NumPy Developers. [`numpy.mean`](https://numpy.org/doc/stable/reference/generated/numpy.mean.html).
