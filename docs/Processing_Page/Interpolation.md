---
layout: default
title: Interpolation
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Interpolation/
nav_order: 1
math: katex
---

# Interpolation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Interpolation is a critical feature in the application that allows users to resample their spectral data, particularly Ramanshift values, to ensure they align with a uniform set of integers. This process is essential for maintaining consistency across datasets, especially when comparing spectra with slightly different measurement intervals. By rounding Ramanshift values to the nearest integer and recalculating the corresponding intensity values, the application ensures that the data is smoothly and accurately represented.

## How to Use

To interpolate your data:

0. Upload data and select spectra you want to process.
1. Navigate to sidebar and turn on the "Interpolation" toggle.
2. Click on Process button on the bottom of the sidebar.

## Behavior

The expected behavior of this feature is that, after interpolation, the spectral data will have its Ramanshift values adjusted to a common set of integer values, with corresponding intensity values recalculated through linear interpolation. This adjustment ensures that all spectra within a dataset can be directly compared or combined, which is particularly useful in various analytical and visualization tasks.

## Method

The mathematical foundation of this interpolation process relies on the [`interp1d`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.interpolate.interp1d.html#scipy.interpolate.interp1d) function from the `scipy.interpolate` module. The function performs a piecewise linear interpolation, which estimates the intensity values at new Ramanshift points based on a linear relationship between neighboring data points in the original dataset.

The interpolation can be represented mathematically as:

$$
I(x) = I(x_i) + \frac{I(x_{i+1}) - I(x_i)}{x_{i+1} - x_i} \times (x - x_i)
$$

where:
- $I(x)$ is the interpolated intensity at a new Ramanshift value $x$,
- $I(x_i)$ and $I(x_{i+1})$ are the intensities at the original Ramanshift values $x_i$ and $x_{i+1}$,
- $x$ is the new Ramanshift value to which interpolation is applied,
- $x_i$ and $x_{i+1}$ are the original Ramanshift values that bracket $x$.

This method effectively smooths the data, filling in gaps and creating a more consistent dataset for further analysis. The `interp1d` function from `scipy.interpolate` is a robust and efficient tool for implementing this interpolation, making it well-suited for processing spectral data.

