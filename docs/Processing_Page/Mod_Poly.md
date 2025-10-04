---
layout: default
title: ModPoly
parent: Baseline Removal
grand_parent: Processing Feature
great_grand_parent: Processing Page
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

## How to Use

To use ModPoly for baseline removal:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Baseline Removal" toggle.
2. Select "ModPoly" from the drop-down menu.
3. Configure parameters:
    - Set polynomial degree (defaults to `5`) - determines the degree of the polynomial fit used for basline correction.

## Behavior

ModPoly fits a polynomial function to estimate and subtract the baseline from the spectra.

A polynomial function with degree specified by the user is iteratively fitted to the data until it either stops making sufficient progress each iteration or reaches the maximum number of iterations. This polynomial is treated as the baseline and subtracted from the original data.
