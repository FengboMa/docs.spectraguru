---
layout: default
title: Peak Identification
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Peak_Identification/
nav_order: 5
---

# Peak Identification and Stats
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

The peak identification feature marks the most significant peaks in intensity from the average spectrum. The identified peaks are based on a few user-specified parameters, namely height, threshold, distance, prominence, and width. Each identified peak is listed in a table detailing that peak’s exact Raman shift, intensity, width, prominence, etc. This feature can be used to get specific information about the most important spikes in intensity seen in the spectral data.

## How to Use

0. In the analytics page, after processing your data, select “Peak Identification and Stats” from the drop-down menu on the left sidebar.
1. By default, “Auto Peak Identification” is turned on. In this case, peaks are sorted by prominence and only a certain number of them are highlighted. To edit this number, adjust the counter labeled “Number of Peaks to identify.”
2. If you would like to filter peaks manually, turn off the toggle labeled “Auto Peak Identification.” Five textboxes will appear, prompting the user to enter filters for height, threshold, distance, prominence, and width.
3. The identified peaks will be marked with a red dot on a line plot of the average spectrum. Below the plot, a table containing detailed information about each peak is displayed.

## Definitions

- Peaks are defined as any data point exhibiting a higher intensity than both the next and previous point.
- Peaks can have many properties. Some of the terminology is explained below:
    0. A peak's *base* is defined as the lowest point between the peak and the first higher peak in a given direction. If there is no higher peak, the edge of the data is considered the next peak.
    1. A peak’s *prominence* is defined as the difference between the peak intensity and the intensity of the highest base.
    2. A peak’s *height* simply refers to the peak intensity.
    3. A peak’s *width* is estimated using the points to either side of the peak where it loses half of its prominence height.
    4. The *threshold* is the minimum difference between the peak intensity and the intensity of the neighboring data entries.
    5. The *distance* is the minimum difference between the Raman shift values of the identified peaks. If two peaks are too close together, the shorter one will be removed.

## Behavior

- Peak identification: SpectraGuru uses SciPy's [`find_peaks`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.find_peaks.html) function to identify peaks. By default, the Peak Identification page selects the `N` most prominent peaks to analyze, where `N` is the preferred number of peaks (specified by the user). Otherwise, if the "Auto Peak Identification" toggle is turned off, the user is prompted to enter values for the required height, threshold, distance, prominence, and width. Each peak must satisfy all of these requirements to be listed in the statistics table.
- Statistics table: The identified peaks are displayed in a table at the bottom of the page, sorted by prominence. This table lists each peak's...
    0. Raman frequency shift (${cm}^{-1}$).
    1. Peak intensity ($a.u.$).
    2. Left and right threshold values.
    3. Prominence height.
    4. Left and right bases.
    5. Width.
    6. Width height (the height at which half the prominence height is lost).


