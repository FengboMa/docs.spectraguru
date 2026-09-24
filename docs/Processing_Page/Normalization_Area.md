---
layout: default
title: Normalization by Area
parent: Normalization
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Normalization/Normalization_Area
nav_order: 1
---

# Normalization by Area
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Normalization by Area rescales each spectrum by its integrated area so spectra with different total signal levels can be compared.

## How to use

To normalize your data by area:

0. Upload data and select the spectra to be processed.
1. Navigate to the sidebar and turn on the "Normalization" toggle.
2. Select "Normalize by area" from the drop-down menu.
3. Leave "Scale factor" at `1` for no additional scaling, or choose an integer from `1` to `100000` to multiply the normalized intensities by that constant.
4. Click "Process" to update the display.

## Behavior

Normalizing by area is good for standardizing data with different measurement conditions. With the default scale factor of `1`, the magnitude of the integrated area is `1`; for a positive-area spectrum, the area itself is `1`. The area is calculated using a trapezoidal sum. A scale factor $c$ multiplies every normalized intensity by the same constant, so the magnitude of the resulting area is $c$. Mathematically, the normalized intensity $S(x)$ at Raman shift $x$ is determined by:

$$
S(x)=c\frac{I(x)}{\left|\sum_{i=1}^n \frac{1}{2}\left(I(x_i)+I(x_{i-1})\right)\left(x_i-x_{i-1}\right)\right|}
$$

where $I(x)$ is the intensity observed at Raman shift $x$, $n$ is the number of Raman shift intervals, and $c$ is the scale factor (default `1`).

## Method

The implementation divides each selected spectrum by the absolute value of its trapezoidal area over Raman shift, then multiplies by the scale factor:

$$I_{\text{norm}}(x)=c\frac{I(x)}{\left|\int I(x)\,dx\right|}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Method choice | Tunable | Selected as **Normalize by area** |
| Scale factor | Tunable | Default `1` (no additional scaling); integer from `1` to `100000` multiplying normalized intensities |
| Integration | Fixed | Trapezoidal area using the Raman shift column |

## References

1. SpectraGuru implementation, self-implemented area normalization.

---

[Back to Normalization](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Normalization/)
