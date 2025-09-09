---
layout: default
title: Average Plot
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Average_Plot/
nav_order: 1
---

# Average Plot with Original Spectra
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

Average plot is a simple yet effective way to visualize processed data and detect overall trends. The plot optionally includes the original spectra in lighter colors for additional reference. This feature allows the user to determine which spectra lie close to or far from the mean, as well as exaggerate commonalities between the spectra. There is also an optional graph that plots the standard deviation between all the samples at each Raman frequency shift.

## How to Use

0. In the analytics page, after processing your data, select “Average Plot with Original Spectra” from the drop-down menu on the left sidebar.
1. Select whether you would like to see the original spectra plotted behind the average spectrum.
2. Select whether you would like to see a graph of the standard deviation at each Raman frequency shift.
3. To download the average plot data, click the button at the bottom of the page labeled “Download Avg and Std data as CSV,” which will write the data to a comma-separated list.

## Behavior

- Average plot: At each Raman frequency shift, this function determines the mean intensity between all samples and graphs the result as a bold blue line. Mathematically speaking, the average intensity graph $\overline{I}(x)$ is determined by the following equation: $\overline{I}(x)=\frac{1}{N}\sum_{i=1}^N I_i(x)$, where $I_i(x)$ is the intensity of spectrum $i$ at Raman shift $x$ $[{cm}^{-1}]$, and $N$ is the total number of samples.
- Selected spectra: If the “Show spectra you selected” toggle is on, each spectrum $I_i(x)$ is plotted with light colors behind the average plot.
- Standard deviation graph: If the “Show Standard Deviation” toggle is on, the standard deviation between all selected spectra is determined for each Raman shift value and plotted on a separate graph below the average plot graph. Mathematically speaking, the standard deviation graph $\sigma(x)$ is determined by the following equation: 

$$
\sigma(x)=\sqrt{\frac{1}{N-1}\sum_{i=1}^N {\left(I_i(x)-\overline{I}(x)\right)}^2}
$$

> where $I_i(x)$ is the intensity of spectrum $i$ at Raman shift $x$ $[{cm}^{-1}]$, and $N$ is the total number of samples.
