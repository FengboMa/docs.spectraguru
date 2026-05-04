---
layout: default
title: SNIP
parent: Baseline Removal
grand_parent: Processing Feature
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/SNIP/
nav_order: 5
---

# SNIP Baseline Removal
{: .no_toc }

## How to use

1. Upload data, then open **Processing Page**.
2. Enable **Baseline Removal**.
3. In **Select your baseline removal function**, choose **SNIP**.
4. Set **SNIP Iterations**.
5. Apply the processing workflow to subtract the estimated baseline.

## Behavior

SNIP estimates a slowly varying background by iteratively clipping peaks from a transformed spectrum. Increasing **SNIP Iterations** allows the baseline estimate to remove wider peak structures, usually producing a smoother and lower background.

## Method

SpectraGuru applies a log-log-square-root transform before iterative clipping:

$$v = \log(\log(\sqrt{\max(y,0)+1}+1)+1)$$

The clipping update replaces each point with the smaller of the current value and the average of points at a symmetric offset:

$$v_i \leftarrow \min\left(v_i,\frac{v_{i-k}+v_{i+k}}{2}\right)$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| SNIP Iterations | Tunable | Default `50`, UI range `10`-`200` |
| Transform | Fixed | Log-log-square-root transform with inverse transform after clipping |
| Baseline action | Fixed | Estimated baseline is subtracted from each selected spectrum |

## References

1. Morhac, M., Kliman, J., Matousek, V., Veselsky, M., & Turzo, I. (1997). Background elimination methods for multidimensional coincidence gamma-ray spectra. *Nuclear Instruments and Methods in Physics Research Section A*, 401(1), 113-132. https://doi.org/10.1016/S0168-9002(97)01023-1
