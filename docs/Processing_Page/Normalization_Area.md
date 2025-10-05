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

## How to Use

To normalize your data by area:

0. Upload data and select the spectra to be processed.
1. Navigate to the sidebar and turn on the "Normalization" toggle.
2. Select "Normalize by area" from the drop-down menu.
3. Click "Process" to update the display.

## Behavior

Normalizing by area is good for standardizing data with different measurement conditions. This method rescales each data point so that the total area under the spectrum curve is `1`. The area is calculated using a trapezoidal sum. Mathematically, the normalized intensity $S(x)$ at Ramanshift $x$ is determined by:

$$
S(x)=\frac{I(x)}{\sum_{i=1}^n \frac{1}{2}\left(I(x_i)+I(x_{i-1})\right)\left(x_i-x_{i-1}\right)}
$$

where $I(x)$ is the intensity observed at Ramanshift $x$, and $n$ is the number of Ramanshift values observed for a given spectrum.
