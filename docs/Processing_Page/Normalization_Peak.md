---
layout: default
title: Normalization by Peak
parent: Normalization
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Normalization/Normalization_Peak
nav_order: 2
---

# Normalization by Peak
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to Use

To normalize your data by peak:

0. Upload data and select the spectra to be processed.
1. Navigate to the sidebar and turn on the "Normalization" toggle.
2. Select "Normalize by peak" from the drop-down menu.
3. Click "Process" to update the display.

## Behavior

Normalizing by peak is good for understanding and comparing peak structure. This method rescales each data point so that the highest peak has an intensity of `1`. Mathematically, the normalized intensity is calculated as follows:

$$
S(x)=\frac{I(x)}{I_{\text{max}}}
$$

where $I_{\text{max}}$ is the peak intensity for a given spectrum.

---

[Back to Normalization](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Normalization/)
