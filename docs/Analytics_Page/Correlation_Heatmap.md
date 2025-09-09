---
layout: default
title: Confidence Interval Plot
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Confidence_Interval_Plot/
nav_order: 4
---

# Average Plot with Original Spectra
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

The correlation heatmap is another visualization tool used to show how closely overall trends in each spectrum match with each other spectrum. The user is allowed to set a specific range of interest for the correlation values as well as download the data as a comma-separated list (csv) file. The heatmap uses the Pearson Correlation Coefficient as the correlation value.

## How to Use

0. In the analytics page, after processing your data, select “Correlation Heatmap” from the drop-down menu on the left sidebar.
1. Select whether you would like to set a specific range of interest for the correlation values using the toggle labeled “Customize Heatmap scale.” If activated, additional textboxes will appear requesting a minimum and maximum value.
2. To download the heatmap values, click the button at the bottom of the page labeled “Download Correlation Matrix as CSV,” which will write the data as a comma-separated list.

## Behavior

- Correlation values: For each pair of spectra (the average spectrum is also included), the Pearson Correlation Coefficient is calculated and displayed on the heatmap in a grid according to that pair of spectra. The average spectrum is represented by the final row and final column of the heatmap. SpectraGuru uses Pandas’ built-in correlation function [`pandas.DataFrame.corr`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.corr.html) to create the heatmap, which uses the Pearson Correlation Coefficient by default, which is defined by the covariance divided by the product of standard deviations. Mathematically, the coefficient ] between spectra ] and ] is determined as follows: ], where ] is the intensity of the ] spectra at Raman shift ] and ] is the average intensity of the ] spectra. The closer this value is to 1, the greater the correlation between the corresponding spectra.

- Heatmap scale: The user can change the heatmap scale, which represents the range of expected correlation values. If the “Custom Heatmap scale” toggle is on, heatmap coloring will be based on the value of each correlation coefficient relative to the custom range.

- Display: Each correlation value is displayed on a square grid with side length ], where ] is the number of selected spectra (the extra grid space comes from the average spectrum). If the grid size is greater than `10`, the numerical values of the correlation coefficients will not be displayed in order to avoid clutter. The color of each grid space ranges from light yellow to dark red, where darker, redder colors represent high correlation values.
