---
layout: default
title: ModPoly
parent: Baseline Removal
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/Mod_Poly/
nav_order: 2
---

# Modified Polynomial Fitting (ModPoly)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Modified Polynomial Fitting (ModPoly) estimates a spectral baseline with a polynomial curve and subtracts it from selected spectra.

## How to use

To use ModPoly for baseline removal:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Baseline Removal" toggle.
2. Select "ModPoly" from the drop-down menu.
3. Configure parameters:
    - Set polynomial degree (defaults to `5`) - determines the degree of the polynomial fit used for basline correction.

## Behavior

ModPoly fits a polynomial function to estimate and subtract the baseline from the spectra.

A polynomial function with degree specified by the user is iteratively fitted to the data until it either stops making sufficient progress each iteration or reaches the maximum number of iterations. This polynomial is treated as the baseline and subtracted from the original data.

## Method

ModPoly estimates the baseline as a polynomial of user-selected degree:

$$b(x)=\sum_{k=0}^{d} a_k x^k$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| ModPoly Polynomial degree | Tunable | Default `5`, UI range `1`-`20` |
| Baseline action | Fixed | Fitted baseline is subtracted from each selected spectrum |

## References

1. Lieber, C. A., & Mahadevan-Jansen, A. (2003). Automated method for subtraction of fluorescence from biological Raman spectra. *Applied Spectroscopy*, 57(11), 1363-1367. https://doi.org/10.1366/000370203322554518

---

[Back to Baseline Removal](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Baseline_Removal/)
