---
layout: default
title: Normalization
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Normalization/
nav_order: 6
---

# Normalization
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The Normalization function in SpectraGuru standardizes spectral data and eliminates scale-dependent variations, ensuring that spectra with different intensities or measurement conditions can be meaningfully compared. SpectraGuru offers three normalization methods: area-based, peak-based, and extremes-based.

## How to Use

0. Upload data and select the spectra to be proceseds.
1. Navigate to the sidebar and turn on the "Normalization" toggle.
2. Select a normalization method from the drop-down menu:
    - Normalize by area
    - Normalize by peak
    - Min/max normalize
3. Click "Process" to update the display.

## Behavior

The normalization feature rescales your data to follow a standard so that it can be meaningfully compared to other data. That standard varies based on which of the following three methods is chosen:
- Normalize by area: Rescales each data point so that the total area under the spectrum curve is `1`. The area is calculated using a trapezoidal sum. Mathmatically, the normalized intensity $S(x)$ at Ramanshift $x$ is determined by:

    $$
    S(x)=\frac{1}{I(x)}\sum_{i=1}^n \frac{1}{2}\left(I(x_i)+I(x_{i-1})\right)\left(x_i-x_{i-1}\right)
    $$

    where $I(x)$ is the intensity observed at Ramanshift $x$, and $n$ is the number of Ramanshift values observed for a given spectrum.
- Normalize by peak: Rescales each data point so that the highest peak has an intensity of `1`. Mathematiaclly, the normalized intensity is calculated as follows:

    $$
    S(x)=\frac{I(x)}{I_{\text{max}}}
    $$

    where $I_{\text{max}}$ is the peak intensity for a given spectrum.
- Min/max normalize: Shifts each spectrum downward so that the minimum is at `0`, then rescales the data so that the maximum is at `1`. Mathematically, the normalized intensity is derived by:

    $$
    S(x)=\frac{I(x)-I_{\text{min}}}{I_{\text{max}}-I_{\text{min}}}
    $$

    where $I_{\text{max}}$ is the peak intensity and $I_{\text{min}}$ is the minimum intensity.
