---
layout: default
title: Normalization by Min/Max
parent: Normalization
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Normalization/Normalization_Minmax
nav_order: 3
---

# Normalization by Min/Max
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to Use

To normalize your data by minimum & maximum:

0. Upload data and select the spectra to be processed.
1. Navigate to the sidebar and turn on the "Normalization" toggle.
2. Select "Min max normalize" from the drop-down menu.
3. Click "Process" to update the display.

## Behavior

Normalizing by min and max is good for filtering data for machine learning and/or statistical analysis. This method shifts each spectrum downward so that the minimum is at `0`, then rescales the data so that the maximum is at `1`. Mathematically, the normalized intensity is derived by:

$$
S(x)=\frac{I(x)-I_{\text{min}}}{I_{\text{max}}-I_{\text{min}}}
$$

where $I_{\text{max}}$ is the peak intensity and $I_{\text{min}}$ is the minimum intensity.

---

[Back to Normalization](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Normalization/)
