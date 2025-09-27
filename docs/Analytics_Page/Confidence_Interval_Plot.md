---
layout: default
title: Confidence Interval Plot
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Confidence_Interval_Plot/
nav_order: 2
---

# Confidence Interval Plot
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

The confidence interval plot is a concise way to view both the mean intensities and standard deviations all at once. This feature creates a plot of the average spectrum and includes a light blue region around the line representing a spread of one standard deviation from the mean. This is useful for visualizing which Raman shifts result in the most or least variation (potentially noise) between the selected spectra.

## How to Use

0. In the analytics page, after processing your data, select “Confidence Interval Plot” from the drop-down menu on the left sidebar.
1. The bold blue line represents the average spectrum, and the light blue region represents values within one standard deviation from the mean.

## Behavior

Both the average spectrum and standard deviation values are calculated via the same methods as in the “Average Plot with Original Spectra” feature discussed previously. See related documentation [here](/Analytics_Page/Analytics_Features/Average_Plot/).

- Confidence interval: The bounds of the light blue region are calculated by adding/subtracting the standard deviation to/from the average spectrum. Mathematically speaking, the upper bound line $U(x)$ is determined by $U(x)=\overline{I}(x)+\sigma(x)$, and the lower bound line $L(x)$ is determined by $L(x)=\overline{I}(x)-\sigma(x)$, where $\overline{I}(x)$ is the average intensity of the spectra at Raman shift $x$ $[{cm}^{-1}]$, and $\sigma(x)$ is the standard deviation.