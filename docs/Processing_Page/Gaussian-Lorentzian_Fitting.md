---
layout: default
title: Gaussian-Lorentzian Fitting
parent: Baseline Removal
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/Gaussian-Lorentzian_Fitting/
nav_order: 3
---

# Gaussian-Lorentzian Fitting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to Use

To use Gaussian-Lorentzian Fitting for baseline removal:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Baseline Removal" toggle.
2. Select "Gaussian-Lorentzian Fitting" from the drop-down menu.
3. Configure parameters:
    - Choose the number of fitting ranges to use.
    - Use the textboxes that appear to set the bounds of those ranges.
    - Click "Apply fitting ranges" to apply the values specified.

## Behavior

Gaussian-Lorentzian fitting uses a Gaussian-Lorentzian hybrid to fit to the data and find a baseline.

A hybrid of both a Gaussian and Lorentzian curve is fitted to the data in each range to determine the baseline. A Gaussian curve takes the following mathematical form:

$$
A e^{-\frac{(x-p)^2}{2\sigma^2}}
$$

where $A$ is the amplitude of the peak of the curve, $p$ represents the location of the peak, and $\sigma$ represents the standard deviation of the peak (related to its width). A Lorentzian curve looks similar but takes a different mathematical form:

$$
\frac{S}{\pi} \cdot \frac{\gamma}{(x-p)^2+\gamma^2}
$$

where $S$ is the area under the curve, and $\gamma$ is related to the width of the peak. The Gaussian and Lorentzian curves are combined simply by adding them together; this is the curve tweaked by the algorithm to be fitted to your data and subtracted off as a baseline.

---

[Back to Baseline Removal](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Baseline_Removal/)
