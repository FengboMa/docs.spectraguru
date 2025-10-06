---
layout: default
title: AirPLS
parent: Baseline Removal
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/AirPLS/
nav_order: 1
---

# Adaptive Iteratively Reweighted Penalized Least Squares (AirPLS)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to Use

To use AirPLS for baseline removal:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Baseline Removal" toggle.
2. Select "AirPLS" from the drop-down menu.
3. Configure parameters:
    - Set lambda (defaults to `100`) - controls the smoothness of the estimated baseline.
    - Set p-order (defaults to `1`) - defines the penalty order for iterative reweighting.
    - Set max iterations (defaults to `15`) - determines the maximum number of fitting iterations.
    - Set tolerance (tau) (defaults to `0.0010`) - sets the convergence criterion for stopping iterations.

## Behavior

AirPLS iteratively adjusts the baseline using a penalized least squares approach to smooth the background while preserving peaks.

A background vector is repeatedly adjusted according to how well it fits with a *weighted* version of the data. The weights change each iteration, and peaks in the data are intentionally given low weights so that they are less likely to be interfered with after baseline removal. AirPLS keeps refining the background vector until it is within the tolerance (tau) of the weighted data or it has reached the maximum number of iterations.

## References

The AirPLS algorithm that SpectraGuru uses is a translation of the R source code from AirPLS version 2.0 by Yizeng Liang and Zhang Zhimin, which can be found at <https://code.google.com/p/airpls>.

1. Z.-M. Zhang, S. Chen, and Y.-Z. Liang, Baseline correction using adaptive iteratively reweighted penalized least squares. Analyst 135 (5), 1138-1146 (2010).

---

[Back to Baseline Removal](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Baseline_Removal/)
